##マイグレーション
>tableの変更を適用し、作成する
```
rails db:migrate
```
>直前のtableをdownにする
```
rails db:rollback
```
>tableがupかdownかを確認
```
rails db:migrate:status
```
>特定のマイグレーションファイルをdown(upも同じ)
```
rails db:migrate:down VERSION=作成日
```
>全てのマイグレーションファイルをdownにしてから再度upにする
```
rails db:migrate:reset
```