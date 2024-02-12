##アプリケーションのテスト
>テスト駆動開発のサイクル
1. 失敗するテストを最初に書く
2. 次にアプリケーションのコードを書いて成功させる
3. 必要ならリファクタリング
```
rails test
```
- コントローラを作成すると自動でテストファイルも作成される
```
require 'test_helper'
class StaticPagesControllerTest < ActionDispatch::IntegrationTest
  test "should get home" do     #テスト名
    get static_pages_home_url   #テストするページのurlを指定
    assert_response :success    #受け取ったレスポンスが成功してるかどうか検証
  end
  test "should get help" do
    get static_pages_help_url
    assert_response :success
  end
end
```
>統合テスト
- アプリケーション全般をテストできる
テストファイル作成
```
rails g integration_test site_layout
```
test/integration/site_layout_test.rb
```
require 'test_helper'

class SiteLayoutTest < ActionDispatch::IntegrationTest

  test "layout links" do                              #テスト名
    get root_path                                     #get root_pathを実行
    assert_template 'static_pages/home'               #テストするページがstatic_pages/homeかどうかを検証
    assert_select "a[href=?]", root_path, count: 2    #root_pathへのリンクが2つ存在するか検証
    assert_select "a[href=?]", help_path              #help_pathへのリンクが存在するか検証
    assert_select "a[href=?]", about_path             #about_pathへのリンクが存在するか検証
    assert_select "a[href=?]", contact_path           #contact_pathへのリンクが存在するか検証
  end
end
```
統合テスト実行
```
rails test:integration
```