## active_storage
- インストール
```
rails active_storage:install
rails db:migrate
```

- 名前を付けて使用する
```
has_one_attached :image
```

### active_storageの画像のサイズ変更
```
def get_image(width, height)
  if image.attached?
    image.variant(resize_to_limit: [width, height]).processed
  else
    "no_image"
  end
end
```