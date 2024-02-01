# helper
helperはviewに対応するメソッドをまとめることができる  
if文等の条件分岐を複数使用する際はエラーを防ぐためにhelperに記述
```

  def my_user?(user)
    user == current_user
  end

  def strftime(time)
    time.in_time_zone("Asia/Tokyo").strftime("%Y/%m/%d")
  end

  def strftime_sec(time)
    time.in_time_zone("Asia/Tokyo").strftime("%Y/%m/%d %H:%M:%S")
  end
```

