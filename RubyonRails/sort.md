## ソート機能
>modelに記述
- 新着順、古い順
```
scope :latest, -> { order(created_at: :desc )}
scope :old, -> {order(created_at: :asc )}
```
- いいね順、コメント順
```
scope :favorite_count, -> {Post.includes(:favorites).sort{ |a,b| b.favorites.size <=> a.favorites.size }}
scope :comment_count, -> {Post.includes(:comments).sort{ |a,b| b.comments.size <=> a.comments.size }}
```
>controllerに記述
```
if params[:latest]
  Post.latest
elsif params[:old]
  Post.old
elsif params[:favorite_count]
  Post.favorite_count
elsif params[:comment_count]
  Post.comment_count
else
  Post.all
end
```
>viewに記述
```
<%= link_to "新着順", posts_path(latest: true) %>
<%= link_to "古い順", posts_path(old: true) %>
<%= link_to "いいね順", posts_path(favorites_count: true) %>
<%= link_toi "コメント順", posts_path(comments_count: true) %>
```