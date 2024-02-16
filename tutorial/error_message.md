##エラーメッセージ
app/views/shared/_error_messages.html.erb
```
<% if @user.errors.any? %>      #エラーの存在をチェック
  <div id="error_explanation">
    <div class="alert alert-danger">
      The form contains <%= pluralize(@user.errors.count, "error") %>.  
      最初の引数に整数が与えられると、それに基づいて2番目の引数の英単語を複数形に変更したものを返す
    </div>
    <ul>
    <% @user.errors.full_messages.each do |msg| %>
      <li><%= msg %></li>
    <% end %>
    </ul>
  </div>
<% end %>
```