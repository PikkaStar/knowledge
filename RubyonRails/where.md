## find、find_by、where
### find
- 1件のidデータを取得する際に使用  
URLのidを1件取得 
```
@user = User.find(params[:id])
```
### find_by
- 指定したカラムデータを1件取得
```
@user = User.find_by(name: "山田太郎")
@post = Post.find_by(title: "タイトル", body: "テスト")
```
### where
- 指定したカラムデータを全て取得
```
@user = User.where(name: "山田")
@post = Post.where(title: "タイトル", body: "テスト")
```