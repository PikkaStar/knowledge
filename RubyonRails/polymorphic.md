## ポリモーフィック関連付けを利用して通知機能(フォロー時、いいね時)
- ポリモーフィックとは1つのモデルが複数のモデルと関連づけることができる仕組みのこと
notificationテーブル
```
t.references :user, null: false, foreign_key: true
t.references :notifiable, polymorphic: true, null: false
t.boolean :read, default: false, null: false
```
- referencesを使用するとNOT NULL制約や、外部キー制約のオプションを自動で設定
- t.references :userでnotificationテーブルにuser_idカラムが作成
- t.references :notifiable, polymorphic: trueとすることで、notifiableのカラムにnotifiable_typeとnotifiable_idが追加される
- booleanはtrueかfalseのどちらかを扱う。defaultを設定しないとtrue/false/nullのいずれかになってしまう。
### modelに関連付けの記述
#### notification.rb
```
belongs_to :user
belongs_to :notifiable, polymorphic: true
```
- belongs_to :notifiable, polymorphic: trueとするとポリモーフィック関連として設定され、複数のnotifiableモデルに属することを設定
#### post.rb
```
has_many :favorites, dependent: :destroy
has_many :notifications, as: :notifiable, dependent: :destroy
```
- as: :notifiableとすることでpostモデルがnotificationモデルに紐づくモデルということを認識する
#### favorite.rb
```
has_one :notification, as: :notifiable, dependent: :destroy
```
- favotiteモデルに紐づく通知は1つなのでhas_oneで関連付け
ここまででpostモデルとfavoriteモデルはnotifiableモデルとして扱う、notificationモデルはnotifiableモデルに属する、という設定をした。
#### user.rb
```
has_many :notifications, dependent: :destroy
```
通知の作成にはActiveRecordのコールバック機能を使用して実装する。
- コールバックとはレコードが作成されたときや更新されたときなど、特定のタイミングで自動的に処理を実行する機能
- 作成時、更新時、削除時に使用できる(今回はafter_create)
- コールバックを実装するにはモデルに記述
#### post.rb
```
after_create do
  user.followers.each do |follower|
    notifications.create(user_id: follower.id)
  end
end
```
- after_create do ... endのように実行タイミングと処理を記述すると、指定されたタイミングでその処理が実行される
- 上記の記述で、postが新規作成された後、post投稿者のフォロワーを取得して、それぞれに対して通知を行う
#### favorite.rb
```
after_create do
  create_notification(user_id: book.user_id)
end
```
- has_one関連づけの場合はcreate_xxxメソッドで関連付けられたレコードを作成できる
### 未読→既読処理
notification.rb
```
def message
  if notifiable_type === "Book"
    "フォローしている#{notifiable.user.name}さんが#{notifiable.title}を投稿しました"
  else
    "投稿した#{notifiable.book.title}が#{notifiable.user.name}さんにいいねされました"
  end
end
def notifiable_path
  if notification.notifiable_type === "Book"
    book_path(notifiable.id)
  else
    user_path(notifiable.user.id)
  end
end
```
- controllerは未読から既読への更新だけなのでupdateのみ
notification_controller
```
def update
  notification = current_user.notifications.find(params[:id])
  notification.update(read: true)
  redirect_to notification.notifiable_path
end
```
- 1行目でログインユーザーに紐づく通知レコードから、指定のidレコードを取得
- 2行目で1行目で取得した通知レコードのreadカラムをtrueに更新
- 3行目で通知内容の種類に応じたリダイレクト
#### view
```
<li class="dropdown">
  <button class="btn btn secondary dropdown-toggle" type="button" id="dropdownMenuButton" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false" %>
   Notification
   <span class="badge badge-danger"><%= current_user.notifications.where(read: false).count %></span>
   </button>
   <div class="dropdown-menu" aria-labelledby="dropdownMenuButton">
    <% if current_user.notifications.where(read: false).any? %>
      <small class="dropdown-item disabled">直近5件の未読の通知を表示</small>
        <% current_user.notifications.where(read: false).limit(5).order(created_at: :desc).each do |notification| %>
          <%= link_to notification.message, notification, method: :patch, class: "dropdown-item" %>
        <% end %>
      <% else %>
        <span class="dropdown-item disabled">未読の通知はありません</span>
      <% end %>
   </div>
</li>
```