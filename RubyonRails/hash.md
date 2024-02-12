##連想配列(ハッシュ)
- キーと値で構成される
```
user = { "first_name" => "Michael", "last_name" => "Hartl" }
=> {"last_name"=>"Hartl", "first_name"=>"Michael"}
user["last_name"]
"Hartl"
```
- キーにはシンボルを使用できる(一部の文字列のみ)
```
user = { :name => "Michael Hartl", :email => "michael@example.com" }
=> {:name=>"Michael Hartl", :email=>"michael@example.com"}
user[:name]
=> "Michael Hartl"
```
- :を後ろに付けるハッシュもある
```
{ name: "Michael Hartl", email: "michael@example.com" }
```
- 例
```
params = {}
params[:user] = { name: "Michael Hartl", email: "mhartl@example.com" }
=> {:name=>"Michael Hartl", :email=>"mhartl@example.com"}
>> params
=> {:user=>{:name=>"Michael Hartl", :email=>"mhartl@example.com"}}
>>  params[:user][:email]
=> "mhartl@example.com"
```
- each文
```
array = {one: "uno",two: "dos",three: "tres"}
array.each do |key,value|
  puts "#{key}はスペイン語で#{value}です"
end
```