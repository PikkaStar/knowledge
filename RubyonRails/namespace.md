## namespace、scope module、scope
### namespace
- pathとURLに名前が付き、controllerのファイルも指定
```
namespace :admin do
  resources :users
end
```
| |  |
|:---:| :---: |
|パス名|admin_users|
|URL|admin/users|
|参照コントローラ|admin/users#index|
### scope module
- pathとURLに名前がつかない。controllerのファイルは指定
```
scope module: :admin do
  resources :users
end
```
| |  |
|:---:| :---: |
|パス名|users|
|URL|users|
|参照コントローラ|admin/users#index|
### scope
- URLにのみ名前がつく
  - controllerはadminの配下ではない
```
scope :admin do
  resources :users
end
```
| |  |
|:---:| :---: |
|パス名|users|
|URL|admin/users|
|参照コントローラ|users#index|
