##今日や昨日のこと
>今日
```
created_at: Time.zone.now.all_day
```
>昨日
```
created_at: 1.day.ago.all_day
```
>6日前から今日
```
created_at: 6.day.ago.beginning_of_day..Time.zone.now.end_of_day
```
>2週間前から1週間前まで
```
created_at: 2.week.ago.beginning_of_day..1.week.ago.end_of_day
```
>過去7日間の1日ごとに作成されたデータを取得
model
```
scope :created_day_ago, ->(n) {where(created_at: n.day.ago.all_day)}
```
view(1日前)
```
<%= @posts.created_days_ago(1).count %>
```