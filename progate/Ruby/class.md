##クラスとインスタンス
- クラス名は大文字で始める
- インスタンスの定義はattr_accessorを使用
```
class Menu      #クラス名
  attr_accessor :name    #インスタンス変数
  attr_accessor :price
end
```
インスタンス生成とデータ入力
```
class Menu           #クラス
	attr_accessor :name   #インスタンス変数
	attr_accessor :price　#インスタンス変数
end
menu1 = Menu.new    #インスタンス生成
menu1.name = "ピザ" #インスタンスデータ定義
puts menu1.name     #ピザ
menu1.price = 800
puts menu1.price    #800
```
initializeメソッドはインスタンスが生成された直後に自動で処理されるメソッド
```
class Menu
  attr_accessor :name
  attr_accessor :price
  def initialize      #インスタンス生成後に処理されるメソッド
    self.name = "ピザ"
    self.price = 800
  end
  def info
    return "#{self.name} #{self.price}円"
  end
  def get_total_price(count)
    total_price = self.price * count
    if count >= 3
      total_price -= 100
    end
    return total_price
  end
end
menu1 = Menu.new　#作成後、自動でinitializeが実行
puts menu1.info    #ピザ　800円
```
initializeメソッドに引数を渡す場合は、インスタンス作成時に渡す
```
class Menu
	def initialize(message)
		puts message
	end
end
menu1 = Menu.new("こんにちは")
```