# リファクタリング

>複数のコントローラーに共通の記述があればconcernに纏める  
**Kaminari.paginate_array**が複数のコントローラーに記述されていたのでconcernに記述
```
module Paginatable
  extend ActiveSupport::Concern

  class_methods do
    def paginate_items(items, page, per)
      Kaminari.paginate_array(items).page(page).per(per)
    end
  end
end
```
>1つのコントローラーに共通の記述があるならmodelに記述(例：いいねソート)  
concernのメソッドを呼び出す。**include Paginatable**
```
include Paginatable

def self.favorite_count(page, per)
    posts = Post.includes(:favorites).sort { |a, b| b.favorites.size <=> a.favorites.size }
    Post.paginate_items(posts, page, per)
end
```
>modelで定義したメソッドをコントローラで使用する。
```
@posts = Post.favorite_count(params[:page],10)
```