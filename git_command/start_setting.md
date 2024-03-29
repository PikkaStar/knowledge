##gitのコマンド
- gitリポジトリの初期化
```
git init
```
- 全てのファイルの変更をステージング(変更の準備)
- 特定のファイルのみをステージング
- ローカル環境に変更を反映
- git add .とgit commit を合わせたコマンド(ファイルを新規追加した場合は不可)
```
git add .
git add ファイル名
git commit -m "コミットメッセージ"
git commit -a -m
```
- ファイルの変更状態を確認
```
git status
```
- コミットメッセージ確認(長い分は「q」を押すと終了する)
- リモートリポジトリに変更を反映
```
git log
git push origin
```
- ブランチ作成
- ローカルブランチ一覧表示
- ブランチ削除
- ブランチ移動
- 変更を破棄してブランチ移動
```
git checkout -b
git branch
git branch -d
git checkout
git checkout -f 作業場名
```
- リモートリポジトリからデータを取得
- 指定したブランチを現在のブランチにマージ

```
git pull origin
git merge
```