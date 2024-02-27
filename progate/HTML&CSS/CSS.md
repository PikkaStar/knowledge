##cssでの適用
>要素を横並び
```
float: left(right);
```
>複数のクラスに同じcssを適用
```
要素1,要素2 {     #,で区切る
  css
}
```
>背景画像
```
background-image:url(画像url)
background-size: cover;  #1枚の画像で表示範囲を埋め尽くす
```
>要素の透明度
```
opacity: 0.5;  #数字が0に近いと透明、1に近いと不透明
```
>背景色の透明度
```
background-color: rgba(50,50,50,1);   #4つ目の値が透明度
```
>文字の太さ
```
font-weight: normal;   #細い
font-weight: bold;  #太い
```
>文字の間隔
```
letter-spacing: 5px;
```
>行の高さ
```
line-height: 30px;  #要素の高さとline-heightの高さが同じだと中央に配置される
```
>マウスカーソルが乗った時にcss適用
```
要素:hover {
  color: red;
}
```
>クリックされてる間だけcss適用
```
要素:active {
  background-color: red;
}
```
>角を丸める
```
border-radius: 10px;
```
>アニメーション
```
要素{
	transition:all 1s;
}
#allは変化の対象、1sは変化の時間
要素:hover{
	background-color: red;
}
```
>ポジション
```
要素 {
  position: absolute;   #サイト全体の左上を基準に、そこからtopやleftで指定
  top: 50px;
  left: 70px;
}
relativeを使用すると、その要素の左上が基準となる
大要素 {
  position: relative; 　　#topやleft等を使用することで、基準位置をずらすことができる
}

大要素の中に入れる小要素 {
  position: absolute;
  top: 20px;
	left: 30px;
}
要素を固定する
要素 {
  position: fixed;
  top: 10px;
  left: 30px;
}
重なり順
要素 {
  position: fixed;
  top: 10px;
  left: 30px;
  z-index: 10;  #数字が大きいほど前に来る
}
```
>影
```
box-shadow: 10px 10px black;　　　#水平方向　垂直方向　色
box-shadow: none;    #影を消す
```