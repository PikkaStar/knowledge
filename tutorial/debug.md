>デバッグ用の情報を表示
開発環境でのみ表示される
```
<%= debug(params) if Rails.env.development? %>
```
>railsの3つの環境
```
test:テスト環境
development：開発環境
production：本番環境
```
>byebug
呼び出された瞬間の状態を確認できる