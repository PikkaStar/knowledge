## enum
>enumとは数字に意味を持たせるものの事
- 次の手順で行う
1. 数字と文字列を紐づける
2. 文字列を日本語化する
3. view等で表示する

>Gemfileに記述してbundle install
```
gem 'enum_help'
bundle install
```
>modelにenumの定義
```
enum payment_method: { credit_card: 0, transfer: 1 }
```
この記述でpayment_methodに0が入っている場合はcredit_card  
1が入っている場合はtransferと定義できる
>日本語化
- config/application.rb
```
config.i18n.default_locale = :ja
```
この記述で、ymlファイルを元に日本語化を行う
>ymlファイルを作成
- config/locales/ja.yml
```
ja:
  enums:
    モデル名:
      payment_method:
        credit_card: "クレジットカード"
        transfer: "現行振込"
```