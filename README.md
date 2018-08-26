# ruby
dotinstll_ruby
ruby

ri コマンド
　コマンドの詳細を観れる

コメント
１行　#
複数行
　=begin
　コメント
　コメント
　コメント
　=end

print：改行なし
puts：改行あり
p：デバッグ用（オブジェクトの種類がわかりやすい）

定数：変更できない変数

インスタンスのどのクラスか
　.classメソッドで確認できる
どんなメソッドがあるか
　.methodsメソッドで確認できる
 
.upcase：文字列を大文字で返す
.upcase!：文字列を大文字で返して下の部分も
　　　　　 大文字に変換する
!：破壊的メソッド

?：真偽値　true or false
.empty?：文字列が空かどうか
.include?(“~”)：特定の文字が含まれているか

分数　Rational(2,5)　⇨　５分の２
　　　2/5r　　　　　 ⇨　ゞ
四捨五入　⇨　.round
小数点以下切り捨て　⇨　.floor
小数点以下切り上げ　⇨　.ceil

“”　特殊文字　式展開可能
‘’　上記はできない
\t　タブ
#{}　rubyでの処理がされる

ハッシュの書き方
変数 = {key => value}
シンボルオブジェクト
:文字列より高速※推奨されてる
変数 = {:key => value}
さらに短い書き方
変数 = {key: value}
ハッシュの参照
変数[:key]　　　=>  value

変数.keys：key一覧
変数.values：value一覧
変数.has_key?(:key)：指定したkeyがあるか

配列
.push(“~~”)：最後尾に追加
　変数 << “~~”　でもOK
.size：要素数
.sort：並び替え

“”の代用
%Q or %q
“”           ‘’
配列時の”” or ‘’
%W(~~ ~~ ~~)：””
%w(~~ ~~ ~~)：’’

%s：文字列
%d：整数
%f：浮動小数点
例）　“name: %s” % “taguchi”
%sの部分が”taguchi”になる
“name: %10s” % “taguchi”：１０桁分
“name: %-10s” % “taguchi”：左寄せ

“id: %05d, rate:%10.2f” % [355, 3.284]
・5桁、満たない場合は０で埋める
・小数点以上は10桁、以下は2桁

if
if 条件 then
  処理
elseif 条件 then
 処理
else
  処理
end

⇦thenは省略可能

ユーザからの入力を受け取る
gets
　文字列で受け取る
gets.to_i　等で変換してやる

signal = gets.chomp
case signal
when “red” then
  puts “stop!”
when “green” ,”blue” then
  puts “go!”
when “yellow” then
  puts “caution!”
else
  puts “wrong signal”
end

ループ
while i < 10 do
 処理
end

timesメソッド
10.times do |i|
  処理
end
※iで回数の管理
↓１行で書くと
10.times { |i| puts “#{i}: hello”}

eachメソッド
範囲.each do |i|
 処理
end

[“red”, “blue”].each do |color|
  処理
end

{ho:200, ge:400}.each do |name, score|
  処理
end

for　doは省略可能
for i in 15..20 do
 処理
end

loop：別に指定しない限り永遠にループする
break：ループを抜ける
next：処理をスキップする

loop do
  処理
end

インスタンス変数の変更
attr_accessor :name
※アトリビュートアクセッサー
#setter: name=(value)
#getter: name

getterのみはattr_reader :name

クラス
　１文字目は大文字で定義
initialize(イニシャライズ)
def initialize(name)
  @name = name
       ↑@nameがインスタンス変数
          pythonのself

インスタンスの生成
変数 = クラス名.new(“引数”)

クラス
　１文字目は大文字で定義
initialize(イニシャライズ)
def initialize(name)
  @name = name
       ↑@nameがインスタンス変数
          pythonのself

インスタンスの生成
変数 = クラス名.new(“引数”)

クラス変数
　クラス全体で使用できる変数
メソッドのアクセス権
　public　デフォルト
　private　initialize, クラス外のメソッド
　　⇨レシーバを指定できない
　　　つまりクラス外から呼び出せない
module
　名前空間

module Movie
  def self.encode
    処理
  end
  def self.export
    処理
  end
end

Movie.encode
Movie.export

module Debug
  def info　⇦　インスタンスメソッド
                         他のクラスにもはめ込める(ミックスイン)
    puts “#{self.class} debug info…”　⇦　
  end　　　　　　　end

class Player
end

class Monster
end

module Debug
  def info　
    puts “#{self.class} debug info…”　
  end
end

class Player
  include Debug
end

class Monster
  include Debug
end

Player.new.info
play = player.new
  play.info

　　インスタンスメソッド
⇦　他のクラスにもはめ込める(ミックスイン)

⇦self.classでこのメソッドを呼び出した
　クラス名が入る
 
 x = gets.to_i

begin
  p 100 / x
rescue => ex
  p ex.message
  p ex.class
  puts "stopped!"
ensure
  処理
end
end

例外処理
例外処理をしたい処理をbegin endで囲む
例外が発生した際にする処理 rescue => ex
  exの中に発生した例外のオブジェクトが入る
  オブジェクトのクラス名が知りたい場合はex.class
  例外が発生してもしなくても行いたい処理はensure
