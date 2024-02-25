##戻り値
呼び出し元で受け取る処理結果の事。
```
def discount(price)
	return price / 2     #戻り値
end
puts "テレビがセール中です！"
half_price = discount(15000)
puts "特別価格で#{half_price}円です"
```
if文でreturnを使用するとtrueかfalseを返す
```
def negative?(number)
	return number < 0  #trueかfalse
end
puts negatice?(5)   #false
```
メソッドを終了させる性質もある
```
def add(a,b)
  return a+ b    #ここで処理が終了
	puts "計算しました"  #処理が実行されない
end
```