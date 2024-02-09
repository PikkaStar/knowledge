##モデルの作成法
```
rails g scaffold
```
- model作成と同時に全アクションのcontroller、view、routeを生成してくれる
- 全アクションが必要な場合は作成の手間が省けるが、不要なアクションがある場合はrails g modelで作成する
```
rails g model
```
- modelとmigrationのみ作成
- 必要なcontroller、route、viewを自分で作成するので無駄がないが、作成の手間はかかる