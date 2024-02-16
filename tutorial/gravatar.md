##gravatar
- プロフィール写真をアップロードして、指定したメールアドレスを関連づけることができる
- GravatarのURLはユーザーのメールアドレスをMD5(暗号学的ハッシュ関数の1つ)という仕組みでハッシュ化している
user/helper
```
# 引数で与えられたユーザーのGravatar画像を返す
def gravatar_for(user)
  gravatar_id = Digest::MD5::hexdigest(user.email.downcase)
  gravatar_url = "https://secure.gravatar.com/avatar/#{gravatar_id}"
    image_tag(gravatar_url, alt: user.name, class: "gravatar")
end
```
表示したいビュー
```
<%= gravatar_for @user %>
```