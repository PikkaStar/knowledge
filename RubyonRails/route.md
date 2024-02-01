## collectionとmember
### collection
- 生成されるURLに:idが含まれない
- users/follow
```
resources :users do
  collection do
    get :follow
  end
end
```

### member
- 生成されるURLに:idが含まれる
- users/:id/follow
```
  resources :users do
    member do
      get :follow
    end
  end
```
