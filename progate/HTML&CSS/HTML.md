##HTMLの基本記述
```
<!DOCTYPE html>  #htmlのバージョンを宣言
<head>
  <meta charset="utf-8"> #文字化けを防ぐ
  <title></title>  #ページのタイトル
  <link rel="stylesheet" href="stylesheet.css">  #cssファイルを読み込む宣言と読み込むcssファイル
</head>
```
>属性
```
<a href="url"></a>  #hrefでリンク先を指定
<img src="url">   #srcで画像のurlを指定
```
>入力欄
```
<input>  #1行の入力欄
<textarea></textarea>  #複数行の入力欄
<input type="submit">  #送信ボタン
<input type="submit" value="保存">  #valueでボタンのテキストを変更
```
>複数のクラスをつける
```
<div class="btn red"></div>  #半角スペースを入れて複数個のクラスを付与する
<div class="btn blue"></div>
```