# elm-lang 的中文手冊 

翻譯自  

http://elm-lang.org/

https://github.com/elm-lang/elm-compiler

#前言介紹

函數式編程 (Functional Programming)像是： Haskell, Scala, Closure 等等被開發出來在各式各樣的專案中使用。
但是，這些語言很少被拿來當成開發前端的工具。而Elm就是為前端人所設計的函數式編程語言

Elm 是一個強型別的函數式編程語言。最終會將它編譯成 JavaScript 以便於在瀏覽器上使用。

* 不會有執行階段錯誤 (Runtime Error)

* Render 的速度快

* 語法簡潔，易於測試

* 完整的錯誤訊息

* 良好的設計架構 (Elm-Architecture)

它與 React 一樣使用了 Virtual DOM 的技術來提高效能並號稱比 React 快

官方的[Learn By example](http://elm-lang.org/examples)

#目錄

1.[安裝](#安裝)

2.[elm工具介紹](#elm-工具)

3.[設定你的Editor的syntax](#編譯器的-elm-syntax)

4.[開始學習Elm](#開始學習elm)

5.[語言核心](#語言核心)

6.[Model in elm](#model-in-elm)

7.[elm的核心架構](#the-elm-architecture)

8.[Signals](#signals)

9.[Interop](#interop)

# 安裝

1.如果您使用Mac 或 Windows 可以直接點選以下連結進行安裝

http://elm-lang.org/install


2.如果您是使用linux OS 可以使用 npm installer 進行安裝
```
npm install -g elm
```

3.如果以上對您都不適用，您也可以選擇從souce去安裝，可參考以下連結

https://github.com/elm-lang/elm-platform#get-haskell-working



----

#elm 工具

接著會開始引導您使用Elm 與 Elm 之一系列工具.

我們假設您已安裝好Elm

####工具

Elm有一系列的工具可幫助您開發Elm程式，在您安裝好Elm時，他們會跟著安裝在您電腦上:

* [Elm](http://elm-lang.org/get-started#elm)

* [elm-package](http://elm-lang.org/get-started#elm-package)

* [elm-make](http://elm-lang.org/get-started#elm-make)

* [elm-repl](http://elm-lang.org/get-started#elm-repl)
 

以下分別介紹，他們的功能

####elm

elm 為啟動其他工具的方式. 試著打開 terminal 並輸入`elm`試試.

如果沒出現任何訊息，請先將以下路徑，加入環境變數

```
C:\Program Files (x86)\Elm Platform\0.16\bin
```

####elm-package

elm-package 是一個套件管理工具, 讓你可以簡單的發佈即安裝套件到Elm Package Catalog.

當你要開始一個新的Elm程式時, 執行:
```
elm package install
```

這將會安裝` elm-core package` 以即將會創造一個 Elm project的檔案: `elm-package.json`

 `elm-package.json` 用來寫一些關於套件相關的訊息，類似一個描述檔

以下為一些常用的 commands:

```
install: 安裝在 elm-package.json 所描述的套件
publish: 將你的 library 發佈到  Elm Package Catalog
bump: 根據 API changes 改變你的版本號碼
diff: 查看兩個 API 的差異
```


####elm-make

elm-make 是在命令列中執行，用來將elm程式編譯為HTML與Javascript. 一般都以此種方式來編譯elm的程式

當我們在編譯時(例如將: Main.elm)編譯為  HTML 檔案 (index.html), 你將會寫出以下指令:

```
elm make Main.elm --output=index.html
```

可用的附加 flags:
```
--warn: Prints warnings to improve code quality
```

####elm-repl

REPL 意思為 `read-eval-print-loop` 讓你可以執行一些簡單的 Elm 語句.  你可以從你的project引入一些程式碼到elm-repl進行測試 ， elm-repl 最終將會轉為javascript程式碼,所以在這之前你需要安裝好 node.js . 需要注意的是 elm-rep只提供 command line interface, browser 相關的 函式 將無法作用.

常用的 commands:

:help: 將會印出提示訊息
:exit: 離開REPL

####elm-reactor

elm-reactor 為Elm的互動式開發工具. 使用 elm-reactor 你可以不用先編譯程式就可以執行 Elm programs，
elm-reactor 還提供了 hot swapping 與 time travel debugging.(類似於redux開發時的功能)

執行 elm reactor時 將會執行一個 web server 於 `0.0.0.0:8000` 你可以開啟你的 browser 選擇你想要執行的程式去執行，
如果你想使用 elm-reactor 更進階的功能, 點擊左側在檔案名稱旁的 wrench ， 之後將會開啟檔案，並且在右方顯示一些功能欄位.

常用的 flags:

-a=<ADDRESS>: 改變 elm-reactor 執行時的ip位置

由於預設的位置 0.0.0.0 不是所有瀏覽器都支援，但我們建議使用` -a=localhost`


-p=<PORT>: 改變 elm-reactor執行時所監聽的PORT

以下為執行的例子
```
elm reactor -a=localhost
打開瀏覽器，輸入 localhost:8000.
```


以上即為elm tools的相關介紹，可以前往https://github.com/elm-lang查看

----

#編譯器的 elm syntax


[Atom](https://atom.io/packages/language-elm)

[Brackets](https://github.com/lepinay/elm-brackets)

[Emacs](https://github.com/jcollard/elm-mode)

[Light Table](https://github.com/rundis/elm-light)

[Sublime Text](https://github.com/deadfoxygrandpa/Elm.tmLanguage)

[Vim](https://github.com/lambdatoast/elm.vim)

[VS Code](https://github.com/sbrink/vscode-elm)

----

#開始學習Elm

##第一個Elm程式

最簡單學習Elm的方式，可從這個連結進入 [範例](http://elm-lang.org/examples). 或是可以試試Elm的[線上編輯器](http://elm-lang.org/try)
或是先前提到的[elm-reactor](https://github.com/elm-lang/elm-reactor)

##進階學習

在官網的 [documentation](http://elm-lang.org/docs) 頁面, 你可以找到許多學習Elm的資源

####1.如果你是剛開始學習Elm
建議你可以到 [Elm Complete Guide](http://elm-lang.org/guide/core-language)進行學習，
並且使用 elm-repl 及 Online Editor來幫助你學習。

####2.如果你想要觀看一些影片來學習
可以到[Pragmatics Studio's Elm tutorial](https://pragmaticstudio.com/elm)

####3.在你閱讀完 Elm Complete Guide後, 你可以接著閱讀
[Elm's Syntax](http://elm-lang.org/docs/syntax) 以及

[Elm's Style Guide](http://elm-lang.org/docs/style-guide). 

(需要注意的是，elm的語句是對縮排敏感的)(類似python)

####4.為了更了解如何開發一個大型的Elm程式，你可以閱讀
[Elm Architecture Tutorial](https://github.com/evancz/elm-architecture-tutorial/)

####5.你也可以到 
[cs223 Functional Programming course](https://www.classes.cs.uchicago.edu/archive/2015/winter/22300-1/Home.html) 
此為芝加哥大學的課程，裡面講了許多有關 Elm 與 純函式編程, 但該課程使用的是 Elm 0.14.1 或許有點跟最新版本的Elm有些差異，但不用擔心，
你可以隨時回來閱讀Elm的syntax與style-guide.

####6.更多的教學
例如 [Elm for the Frontend Right Now](http://bendyworks.com/elm-frontend-right-now/), 
[Checkboard Grid Tutorial](https://github.com/TheSeamau5/elm-checkerboardgrid-tutorial), 
[Building HTML by Parsing Parameters](http://blog.jessitron.com/2015/08/an-elm-example-reading-url-parameters.html) 
在reddit上的討論 [/r/elm](http://reddit.com/r/elm) 以及 [mailing list](https://groups.google.com/forum/?fromgroups#!forum/elm-discuss)


7.但最重要的是，看完後不要忘記自己寫code! 下面是一些簡單的程式，你可以開始試著練習

* 1.寫出一個會偵測你的滑鼠指標位於螢幕的左半邊或右半邊，並且在螢幕中央顯示(左方或右方)的程式。

* 2.寫出一個會在螢幕上隨機位置顯示小黑點的程式，並且帶有重設、暫停、繼續等按鈕

* 3.寫出一個輸入框，讓Gitgub使用者輸入後，可顯示名稱，avatar圖片，與程式語言清單

* 4.寫出一個貪食蛇遊戲(並且可顯示最高分數)


另外: 如果你在寫elm程式時陷入困境,可將你的問題於[mailing list](https://groups.google.com/forum/?fromgroups#!forum/elm-discuss)發問   或是到irc上的 #elm IRC, freenode.net頻道發問。


#語言核心

  [Values](#values)
  
  [Functions](#functions)
  
  [If Expressions](#if-expressions)
  
  [Lists](#list)
  
  [Tuples](#tuples)
  
  [Records](#records)
  
  
#Values

我們先來看一下，下面的例子
```
> "hello"
"hello"

> "hello" ++ "world"
"helloworld"

> "hello" ++ " world"
"hello world"
```
Elm 使用 (++) 來連接字串


Elm的數學部分和其他語言類似

```
> 2 + 3 * 4
14

> (2 + 3) * 4
20

和JavaScript不同， Elm 具有floating point division (/)和 integer division (//)，分別用來計算具有小數或只有整數部分

> 9 / 2
4.5

> 9 // 2
4

```
#Functions
讓我們寫一個 isNegative的函式， 其具有參數可接受數字，並且確認他是否小於零，並返回 True 或 False.
```
> isNegative n = n < 0
<function>

> isNegative 4
False

> isNegative -7
True

> isNegative (-3 * -4)
False

```
和JavaScript、Python、Java的函式寫法不同. 不使用逗點來分隔參數，而是使用空格。

所以 `(add(3,4))` 將為 `(add 3 4)`
此種作法將可避免一個函式的參數區塊具有許多逗點，當你習慣後，你會發現他看起來比較簡潔。 你可以使用 elm-html package 來理解。

#If Expressions

使用條件表達式
```
> if True then "hello" else "world"
"hello"

> if False then "hello" else "world"
"world"
 if then else 用來分隔條件，我們不用再加上任何`{}`符號

需要注意的一點是:Elm 的numbers、strings、lists 不可用來進行類似 boolean 的比較

接著下們的表達式可以用來區別，是否值大於9000

> over9000 powerLevel = \
|   if powerLevel > 9000 then "It's over 9000!!!" else "meh"
<function>

> over9000 42
"meh"

> over9000 100000
"It's over 9000!!!"
```
使用backslash `\` 於 REPL ˋ中，可以讓我們進行斷行，讓function的主要部分寫在名字之後的下一行，可以讓我們更容易閱讀, 
建議在所有functions 和 values 中都用此種寫法去寫。

#List

Lists 是在Elm中最常見的資料結構. 類似於JavaScript 或 Java中的陣列結構,保存一系列的相關同型別資料。

可以查看有關List可以使用的function [List](http://package.elm-lang.org/packages/elm-lang/core/3.0.0/List)
```
> names = [ "Alice", "Bob", "Chuck" ]
["Alice","Bob","Chuck"]

> List.isEmpty names
False

> List.length names
3

> List.reverse names
["Chuck","Bob","Alice"]

> numbers = [1,4,3,2]
[1,4,3,2]

> List.sort numbers
[1,2,3,4]

> double n = n * 2
<function>

> List.map double numbers
[2,8,6,4]
再次強調，List中的每個內容都是相同型別

```
對比一些物件導向語言, Elm 的 functions 和 data 是分開存在的。為了具有模組化 ， Elm 使用了許多模組， 當我們使用` List.isEmpty` 
我們是從List module 中去調用該方法，List module 和lists具有很大的關係。

#Tuples

Tuples 是在Elm中，另外一種很有用的資料結構.tuple 裡面包含一系列的固定值，可以有不同資料型別.當你要從function返回不同資料時可用逗點分隔，
下面的例子中，這個 function會取得 name 並返回一個message給user:
```
> import String

> goodName name = \
|   if String.length name <= 20 then \
|     (True, "name accepted!") \
|   else \
|     (False, "name was too long; please limit it to 20 characters")

> goodName "Tom"
(True, "name accepted!")
```

但是，當你的程式開始變得複雜時，我們會建議使用records來取代 tuples。

#Records

 record 是具有 key-value pairs 的資料結構, 類似於 JavaScript 或 Python中的物件(Object)，你將會發現他在Eml中很好用，
 
 下面有些範例
```
> point = { x = 3, y = 4 }
{ x = 3, y = 4 }

> point.x
3

> bill = { name = "Gates", age = 57 }
{ age = 57, name = "Gates" }

> bill.name
"Gates"
```
 Elm 把 .x (x 為 key 值) 也做成了一個函數，所以我們不只可以用bill.name 也可以用 .name bill 來取得同樣的值。
 ```
 > .name bill
"Gates"

> List.map .name [bill,bill,bill]
["Gates","Gates","Gates"]
```
當 functions 和 records 結合時, 你可以使用以下寫法，更為簡潔
```
> under70 {age} = age < 70
<function> 

> under70 bill
True

> under70 { species = "Triceratops", age = 68000000 }
False
```


從範例中我們可以傳遞任何 record 進去， 當他有一個  number 型態的age field 

It is often useful to update the values in a record.
```
> { bill | name = "Nye" }
{ age = 57, name = "Nye" }

> { bill | age = 22 }
{ age = 22, name = "Gates" }
```
當你更新資料時，Elm不會覆蓋舊資料，而是新建一筆新的record，當你更新十筆資料的其中一筆時，
Elm會用有效率的方式連同其他九筆一同更新。

####比較 Records 與 Objects

Records 在 Elm 類似於 JavaScript的物件(Object), 但有一些關鍵點不同。 以下為records的不同之處:

* 你不可以使用不存在的field.

* field不可為 undefined 或是 null.

* 你不可以使用 this 或 self 等關鍵字來創造遞迴的 records 

Elm 鼓勵你把邏輯和資料分開，因為Elm想把這個在一般物件導向程式中所會遇到的問題避免掉。

Records 也支援 [structural typing](https://en.wikipedia.org/wiki/Structural_type_system)

這個意思為 Elm 在必要的 fields 存在時可以使用在任何情況. 這給我們很大的彈性


#Model in elm


這一章節將帶領你，處理複雜的資料時可以有良好的方式去處理，也可以方便未來去重構，以下將從 “contracts”開始講起。

##Contracts

我們在定義個程式的整體模型時，其中的資料型態占了很重要的部分，想像他們是一份會被編譯器檢查的合約，並且寫著類似“我只接受字串” 
確保不會有其他的資料型態進入。這在 Elm 中是避免執行時期的錯誤是很重要的因素。

注意: 在elm中“types” 意思為 “types as they appear in Elm”.這與 Java 中的type有很大的區別! 許多程序員只有在 Java、JavaScript or Python or Ruby使用type，有時他們覺得type是很不必要的，因為使用的type最後編譯完，還是會得到有關type相關的錯誤訊息
這是什麼原因?

我們寫下的 contracts 為“type annotations” 也是我們寫出我們資料長的什麼樣子的地方。
```
fortyTwo : Int
fortyTwo =
  42


names : List String
names =
  [ "Alice", "Bob", "Chuck" ]


book : { title: String, author: String, pages: Int }
book =
  { title = "Demian", author = "Hesse", pages = 176 }
```
這裡我們寫了一些常會使用到的資料型別， fortyTwo 為一個 integer, names是一個list of strings,而 book 是一個 record with certain fields. 

```
import String


longestName : List String -> Int
longestName names =
  List.maximum (List.map String.length names)


isLong : { record | pages : Int } -> Bool
isLong book =
  book.pages > 400
```

在上面這個範例 longestName ,我們要求輸入的值為一個 list of strings. 假如有人想要輸入一個 list of integers 或是 books, 其中的 String.length function將會中斷,因為我們定義了 contract。我們還指定了 longestName function 將要返回一個 Int ，所以當我們接他的返回值用在其他地方時，可以保證他會是一個數字

其中的isLong example 做的是同樣的事情，他要求一個 record with a field 名稱為 pages 型態為 integers.當其他人輸入任何資料時，都需要一個 pages field!

上面兩個範例中，我們寫了 contracts 說明 “我需要你輸入某種型態的值, 而我也會返回給你同型態的值.” 這將是 Elm 擺脫執行時期發生錯誤的關鍵， 只要我們遵守條件，我們永遠可以知道該function需要什麼型態的值，以及將會返回什麼型態的值。

##Enumerations(列舉)

創造一個自訂的資料型態，並列舉他可能的值，想像我們建造一個 todo list 並且想要再建造一個 filter 來過濾哪些task是看的見的

我們可以如下定義三種顯示方式
```
type Visibility = All | Active | Completed
```

如同上面定義的方式，未來我們要傳遞資料的 type 為 Visibility 時，可能的值只能上面三種的其中一種。

我們使用case-expressions來讓我們在接收到不同的值時做不同的事，和JavaScript 中的switch-statements類似,但 case-expression 不同的是，你不需要在每個case的結尾寫上break

```
toString : Visibility -> String
toString visibility =
    case visibility of
      All ->
          "All"

      Active ->
          "Active"

      Completed ->
          "Completed"


-- toString All == "All"
-- toString Active == "Active"
-- toString Completed == "Completed"
```
這個 case-expression 意思為,如果傳入的 visibility為 All 則回傳"ALL" ，以此類推。

##State Machines(狀態機)

接著我們想要顯示一個使用者是否有登入， 我們可以建造一個小型的state machine 讓使用者可以在匿名以及登入後的使用者名稱做切換。

```
type User = Anonymous | LoggedIn String
```

需要注意的是， LoggedIn 中的值有額外的資訊!意思是當type為LoggedIn 將可接收到一個字串的值. 我們可以
在Anonymous或LoggedIn 使用case-expressions判斷，之後再用 LoggedIn 字串的值，產生不同圖片
```
userPhoto : User -> String
userPhoto user =
    case user of
      Anonymous ->
          "anon.png"

      LoggedIn name ->
          "users/" ++ name ++ "/photo.png"
```

假如他們沒有登入，我們產生"anon.png", 假如他們已登入，即產生對應的圖片. 假設我們現在有數個user，並且想要一次產生他們的圖片

```
activeUsers : List User
activeUsers =
    [ Anonymous
    , LoggedIn "Tom"
    , LoggedIn "Steve"
    , Anonymous
    ]
```

我們可用map的方式，一次產生不同圖片
```
photos =
    List.map userPhoto activeUsers

-- photos =
--     [ "anon.png"
--     , "users/Tom/photo.png"
--     , "users/Steve/photo.png"
--     , "anon.png"
--     ]
```

所有的使用者如此一來都有了對應的圖，這是一個簡單的  state machine 範例， 但你可以想像，假設使用者有五種不同的狀態，我們可以精確的定義好Model，讓錯誤的發生率降低。

##Tagged Unions

接著我們試著把一系列不同的資料型態以緊密的方式結合在一起。或稱(ADTs)

假設我們在主控台上創造一系列的小工具. 其中一個為點陣圖，另一個為 log data，最後一個為時間圖， Type unions 讓他們可以簡單的結合在一起
:

```
type Widget
    = ScatterPlot (List (Int, Int))
    | LogData (List String)
    | TimePlot (List (Time, Int))
```
你可以想像是把三種不同的type放一起. 每個type有一個標籤 ，像是 ScatterPlot 及 LogData.這麼做可以區隔他們. 
接著我們將輸出 widget 如同以下範例:

```
view : Widget -> Element
view widget =
    case widget of
      ScatterPlot points ->
          viewScatterPlot points

      LogData logs ->
          flow down (map viewLog logs)

      TimePlot occurrences ->
          viewTimePlot occurrences
```
根據不同種類的widget， 我們將會輸出不同的東西， 如果我們想要進一歩讓 time plots 展示為一個 logarithmic scale(
對數刻度). 我們可以將 Widget 改為如下

```
type Scale = Normal | Logarithmic

type Widget
    = ScatterPlot (List (Int, Int))
    | LogData (List String)
    | TimePlot Scale (List (Time, Int))
```

現在 TimePlot 有了兩個部分的 data，而每個 tag 可以有不同的 types.

##Banishing NULL

許多語言都有 null 的型態. 每次你覺得你的資料是一個字串，但其實你擁有的只是一個 null， 你需要檢查嗎? 這是否會對你的程式帶來重大影響?下面將會對這類問題進行討論。

Elm 使用了一個 type 叫做 Maybe，來避免了這個問題，你可以想像他把null明確的寫出，所以我們可以知道何時需要去處理他。

```
type Maybe a = Just a | Nothing
```

這個type有一個引數 a ，我們可以對他引用任何想要的值.我們可以使用像是 (Maybe Int) 他將是一個整數或是Nothing。例如， 我們想要把字串解析成月份

```
String.toInt : String -> Result String Int


toMonth : String -> Maybe Int
toMonth rawString =
    case String.toInt rawString of
      Err message ->
          Nothing

      Ok n ->
          if n > 0 && n <= 12 then Just n else Nothing
```

這個 toMonth的 contract 明確的指出他將會返回一個整數，否則將不返回任何東西! 所以你將不用在煩惱會有null的產生。

##Recursive Data Structures(遞迴性的資料結構)

假如你曾經在 C 或 Java中使用過  linked list 你將會認為在 Elm 中使用是很簡單的.下面的是一個list的type. list 的最前面只能接受:
empty或是something followed by a list.我們可將這一個非正式的定義轉為一個 type:

```
type List a = Empty | Node a (List a)
```
所以我們創造一個 type 名為 List.  list 可以是 empty 或是擁有一個 element (the head of the list) 以及 “the rest of the list” ( the tail of the list).

List 接受一個 type 當做 argument, 所以我們可以創造 (List Int) 或是 (List String) 以及其他， 如同以下範例
```
Empty
Node 1 Empty
Node 3 (Node 2 (Node 1 Empty))
```

他們都擁有同樣的 type，所以可以被使用在同個地方。當我們在做 pattern match時 可以定義於 case所要做的事。 假設我們想計算List中所有數字的總和， 下面範例中的 function 定義了一些可能發生的情境。

```
sum : List Int -> Int
sum xs =
    case xs of
      Empty ->
          0

      Node first rest ->
          first + sum rest
```
假設我們得到一個 Empty value, 總和將為 0。 假設我們有一個 Node ，並且將元素一個個加到總合中，將會產生如` (sum (Node 1 (Node 2 (Node 3 Empty))))` 的情況，和下面範例相同:

```
sum (Node 1 (Node 2 (Node 3 Empty)))
1 + sum (Node 2 (Node 3 Empty))
1 + (2 + sum (Node 3 Empty))
1 + (2 + (3 + sum Empty))
1 + (2 + (3 + 0))
1 + (2 + 3)
1 + 5
6
```

接著我們可以試著產生二元樹

```
type Tree a = Empty | Node a (Tree a) (Tree a)
```
A tree 可能為 empty或是一個 node 擁有一個 value 與 two children. 可看下面的範例，來學習更多關於 union types 的資料結構

http://elm-lang.org/examples/binary-tree

>想像我們在 Java 做出這個範例.我們可能會使用 super class 和 兩個 sub classes 來定義二元樹。 想像我們是使用 JavaScript.
一開始看起來不會很困難，但當我們在重構時，你將會遇到許多隱藏的錯誤。

我們也可以 model 一個程式語言為 data ，在這個情況下,他將只處理有關 Boolean algebra:

```
type Boolean
    = T
    | F
    | Not Boolean
    | Or  Boolean Boolean
    | And Boolean Boolean

true = Or T F
false = And T (Not T)
```
當我們 model好可能的值之後，我們可以定義 functions 例如eval 用來執行 Boolean 讓其為 True 或 False，可查看下面的連結範例

http://elm-lang.org/examples/boolean-expressions

#The Elm Architecture

這個教程 “The Elm Architecture” 你將會看到許多跟 [Elm][] 相關的程式, 包含 [TodoMVC][] 、 [dreamwriter][]以及正式上線的  [NoRedInk][] 、 [CircuitHub][]. 了解這個設計模式將對你在 Elm 中的程式或任何其他編程都很有幫助。

[Elm]: http://elm-lang.org/
[TodoMVC]: https://github.com/evancz/elm-todomvc
[dreamwriter]: https://github.com/rtfeldman/dreamwriter#dreamwriter
[NoRedInk]: https://www.noredink.com/
[CircuitHub]: https://www.circuithub.com/

 Elm 架構中的設計模式讓你的元件可以有無限嵌套. 對於模組化、 程式碼復用、 測試很有幫助，最終讓你可以簡單的設計出一個複雜但模組化的web程式。 下面將有八個範例

  1. [Counter](http://evancz.github.io/elm-architecture-tutorial/examples/1.html)
  2. [Pair of counters](http://evancz.github.io/elm-architecture-tutorial/examples/2.html)
  3. [List of counters](http://evancz.github.io/elm-architecture-tutorial/examples/3.html)
  4. [List of counters (variation)](http://evancz.github.io/elm-architecture-tutorial/examples/4.html)
  5. [GIF fetcher](http://evancz.github.io/elm-architecture-tutorial/examples/5.html)
  6. [Pair of GIF fetchers](http://evancz.github.io/elm-architecture-tutorial/examples/6.html)
  7. [List of GIF fetchers](http://evancz.github.io/elm-architecture-tutorial/examples/7.html)
  8. [Pair of animating squares](http://evancz.github.io/elm-architecture-tutorial/examples/8.html)




**注意**: 要運行這些範例需先, [安裝 Elm](http://elm-lang.org/install) 以及 fork this repo. 每個範例都會教導你，該如何去運行它


## Elm中的基本設計模式概念

每個 Elm program 都有如下三個區塊架構:


  * model
  * update
  * view


> 如果你還沒學習過elm可以先參考 [language docs](http://elm-lang.org/docs) 與[the complete guide](http://elm-lang.org/docs#complete-guide)

```elm
-- MODEL

type alias Model = { ... }


-- UPDATE

type Action = Reset | ...

update : Action -> Model -> Model
update action model =
  case action of
    Reset -> ...
    ...


-- VIEW

view : Model -> Html
view =
  ...
```

這個教程都是由上面範例的這個設計模式 與一些小變化及插件所組成的。


## Example 1: A Counter

**[demo](http://evancz.github.io/elm-architecture-tutorial/examples/1.html) / [see code](examples/1/)**

第一個範例是一個簡單的計數器，可以進行增加與減少

[The code](examples/1/Counter.elm) 由一個很簡單的 model所組成， 我們要做的只是追蹤一個會改變的數字

```elm
type alias Model = Int
```

當 model 更新時， 我們定義一系列 actions, 以及一個 `update` function用來接收 actions並執行相應的case

```elm 
type Action = Increment | Decrement

update : Action -> Model -> Model
update action model =
  case action of
    Increment -> model + 1
    Decrement -> model - 1
```

需要注意的是 `Action` [union type][] 並沒有做任何事， 他只是描述了一個動作的型態. 假設有人想讓計數器在點擊某個按鈕時可以讓數字變double, 這將需要增加一個新的 `Action`類型，這可以保持我們的Model簡潔，並且他人可以清楚的知道他可以對這個model進行何種操作

[union type]: http://elm-lang.org/learn/Union-Types.elm

 `view` our `Model`.我們使用 [elm-html][]來創造一個 HTML，其它包含一個 div 裡面裝有一個 decrement button以及a div showing the current count與 an increment button.

[elm-html]: http://elm-lang.org/blog/Blazing-Fast-Html.elm

```elm
view : Signal.Address Action -> Model -> Html
view address model =
  div []
    [ button [ onClick address Decrement ] [ text "-" ]
    , div [ countStyle ] [ text (toString model) ]
    , button [ onClick address Increment ] [ text "+" ]
    ]

countStyle : Attribute
countStyle =
  ...
```
在 `view` 這個函式中的 `Address`我們將會在下一節提到! 在這裡我們使用了 `Model` 並產生一些 `Html`. 我們並沒有手動去更動DOM，
這讓這個 library [有了更好的自由度及優化][elm-html] 並且讓畫面 rendering的速度更快。 以及 `view`是一個function ，我們可使用 Elm中的 module system、 test frameworks與其他 libraries 來創造 views.

這種設計模式是Elm中的基本架構，接著的範例中都是以此種架構去進行 `Model`, `update`, `view`.


## Starting the Program

在elm程式中，都會有一個主體的部分，程式從此開始進行，如同以下的範例均是以 `Main.elm`為主體

```elm
import Counter exposing (update, view)
import StartApp.Simple exposing (start)

main =
  start { model = 0, update = update, view = view }
```

我們使用了 [`StartApp`](https://github.com/evancz/start-app) 來建造初始的 model 、 update 與 view functions. 這即是Elm's [signals](http://elm-lang.org/learn/Using-Signals.elm)的概念，所以你暫時還不用了解signals的概念。

其中的關鍵點在於 `Address`。 每個 event handler 於我們的 `view` function 之中會回傳一個特別的  address. It just sends chunks of data along.而 `StartApp` package 監測每個來自 address 的訊息，並轉送到 `update` function. 接著 model 被更新 ，然後[elm-html][] 把view更新

 Elm 程式中的單向資料流如同下圖的概念

![Signal Graph Summary](diagrams/signal-graph-summary.png)

圖片中的藍色部分為 Elm 程式的核心，此即為我們先前提到的 model/update/view 概念。 未來在寫Elm程式時，即可以此種架構去規劃，讓邏輯的部分完全與View分開。


## Example 2: A Pair of Counters

**[demo](http://evancz.github.io/elm-architecture-tutorial/examples/2.html) / [see code](examples/2/)**

在範例1中，我們建立了一個簡單的計數器。但我們該如何擴展架構，當我們需要兩個計數器時呢? 

 Elm架構中的優點是  **我們可以不更動程式碼**來達成擴展架構。 當我們在上個範例創造 `Counter` 模組時,他把細節封裝起來，所以我們可以把他用在別處。

```elm
module Counter (Model, init, Action, update, view) where

type Model

init : Int -> Model

type Action

update : Action -> Model -> Model

view : Signal.Address Action -> Model -> Html
```

創造模組化的code 是很抽象的。我們把一些 functionality 的部分提供出來並隱藏一些實做細節。在 `Counter` module外面，我們只看得到
一些基本的關於 `Model`, `init`, `Action`, `update`, 與 `view`。我們並不在乎他們是如何被實做的。 事實上,這是不可能被知道的
. 意思是當我們選擇不把他公開時，其他人無法知道我們的實做細節。

所以我們可以複用 `Counter` module，並用他來創造 `CounterPair`，和先前一樣，我們先從 `Model`開始:

```elm
type alias Model =
    { topCounter : Counter.Model
    , bottomCounter : Counter.Model
    }

init : Int -> Int -> Model
init top bottom =
    { topCounter = Counter.init top
    , bottomCounter = Counter.init bottom
    }
```

這個 `Model` 擁有兩個區塊分別為顯示在螢幕的top和bottom。用來完整描述我們應用程式中的 state。 以及一個 `init` function 
讓我們在未來更新`Model`所用。 

接著我們將定義 `Actions` ，將包含: reset all counters、 update the top counter與 update the bottom counter.

```elm
type Action
    = Reset
    | Top Counter.Action
    | Bottom Counter.Action
```

注意到的是，上面的 [union type][] 指向 `Counter.Action` type,但我們並不知道這些 actions，當我們創造 `update` function時， 我們才將
這些 `Counter.Actions` 指向正確的地方:

```elm
update : Action -> Model -> Model
update action model =
  case action of
    Reset -> init 0 0

    Top act ->
      { model |
          topCounter = Counter.update act model.topCounter
      }

    Bottom act ->
      { model |
          bottomCounter = Counter.update act model.bottomCounter
      }
```

最後，我們建造一個 `view` function用來在畫面上顯示兩個 counters 與一個 reset button.

```elm
view : Signal.Address Action -> Model -> Html
view address model =
  div []
    [ Counter.view (Signal.forwardTo address Top) model.topCounter
    , Counter.view (Signal.forwardTo address Bottom) model.bottomCounter
    , button [ onClick address Reset ] [ text "RESET" ]
    ]
```

我們可以重複使用 `Counter.view` function 於兩個 counters. 於每個 counter 我們創造一個 forwarding address.我們在這裡做的事為，這兩個計數器會把傳出的訊息以 `Top` or `Bottom` tag起來，讓我們可以區分。

接著我們還可以讓他更巢狀化，我們可以使用 `CounterPair` module,指對外展示出一些 key values 與d functions, 再創造一個 `CounterPairPair` 或是任何你想要的。


## Example 3: A Dynamic List of Counters

**[demo](http://evancz.github.io/elm-architecture-tutorial/examples/3.html) / [see code](examples/3/)**

接著我們要來創造一系列的計數器，我們可使用add或remove來增加與減少畫面上計數器的數量。

我們一樣複用 `Counter` module ，如同上面的範例。 

```elm
module Counter (Model, init, Action, update, view)
```

接著我們可以直接開始設計 `CounterList` module，和之前一樣 ，先從 `Model`開始:

```elm
type alias Model =
    { counters : List ( ID, Counter.Model )
    , nextID : ID
    }

type alias ID = Int
```

現在我們的model有一系列的counter,每個均擁有一個獨特的ID，讓我們可以區別他們，
(這些 ID 還帶給我們於 rendering時具有最佳化的表現[`key`][key] )

我們的model 還包含了一個`nextID`這可以幫助我們在新增counter時，可以分配新的ID給他

[key]: http://package.elm-lang.org/packages/evancz/elm-html/latest/Html-Attributes#key

現在我們來定義一系列的`Actions` 用來傳給 model。包含了 add counters、 remove counters與update certain counters.

```elm
type Action
    = Insert
    | Remove
    | Modify ID Counter.Action
```


現在我們可以定義`update` function.

```elm
update : Action -> Model -> Model
update action model =
  case action of
    Insert ->
      let newCounter = ( model.nextID, Counter.init 0 )
          newCounters = model.counters ++ [ newCounter ]
      in
          { model |
              counters = newCounters,
              nextID = model.nextID + 1
          }

    Remove ->
      { model | counters = List.drop 1 model.counters }

    Modify id counterAction ->
      let updateCounter (counterID, counterModel) =
            if counterID == id
                then (counterID, Counter.update counterAction counterModel)
                else (counterID, counterModel)
      in
          { model | counters = List.map updateCounter model.counters }
```

可以看下面的描述:

  * `Insert` &mdash; 首先我們創造了一個新的計數器， 放在所有以建造的計數器的最後。
  接著增加 `nextID` 來讓下一次使用。

  * `Remove` &mdash;從許多計數器中移除最前面那個

  * `Modify` &mdash; 找尋這些計數器中與其符合的 ID, 我們在這個符合的計數器上執行這個 `Action`

最後是定義我們的 `view`.

```elm
view : Signal.Address Action -> Model -> Html
view address model =
  let counters = List.map (viewCounter address) model.counters
      remove = button [ onClick address Remove ] [ text "Remove" ]
      insert = button [ onClick address Insert ] [ text "Add" ]
  in
      div [] ([remove, insert] ++ counters)

viewCounter : Signal.Address Action -> (ID, Counter.Model) -> Html
viewCounter address (id, model) =
  Counter.view (Signal.forwardTo address (Modify id)) model
```

有趣的地方在於其中的 `viewCounter` function. 他使用先前的
`Counter.view` function，但這次，我們提供了一個 forwarding address 上面標住了所有被 rendered的counter的相關訊息。

當我們真正創造 `view` function時， 我們對所有counters進行了`viewCounter`的map動作，並且創造兩個按鈕:add 、remove ，直接傳遞到 the `address` 中

上面這種創造 ID的方法，可以用於任何你想要於子組件創造動態數字時，也可應用在其他範例，例如: list of user profiles 、 tweets 或是 newsfeed items 以及 product details中。


## Example 4: A Fancier List of Counters

**[demo](http://evancz.github.io/elm-architecture-tutorial/examples/4.html) / [see code](examples/4/)**

但是，如果我們想要不只是有一個移除按鈕，而是想讓每個按鈕擁有自己專屬的移除按鈕呢? 


要這麼做的話，我們先保持原本的`view` function 不變，並且可以新增一個`viewWithRemoveButton`，如以下範例:
```elm
module Counter (Model, init, Action, update, view, viewWithRemoveButton, Context) where

...

type alias Context =
    { actions : Signal.Address Action
    , remove : Signal.Address ()
    }

viewWithRemoveButton : Context -> Model -> Html
viewWithRemoveButton context model =
  div []
    [ button [ onClick context.actions Decrement ] [ text "-" ]
    , div [ countStyle ] [ text (toString model) ]
    , button [ onClick context.actions Increment ] [ text "+" ]
    , div [ countStyle ] []
    , button [ onClick context.remove () ] [ text "X" ]
    ]
```

`viewWithRemoveButton` function 增加了一個額外的按鈕，其中  increment/decrement 按紐送出訊息到 `actions` address 中，但移除按鈕
送出訊息到 `remove` address中。 在 `remove` 訊息中寫了類似下面的文字, &ldquo;任何擁有我的人請移除我!&rdquo; 

現在我們有了新的 `viewWithRemoveButton`，我們可以建造一個 `CounterList` module 用來放置每個獨立的計數器， 其中 `Model` 和範例3的相同  

```elm
type alias Model =
    { counters : List ( ID, Counter.Model )
    , nextID : ID
    }

type alias ID = Int
```

但這裡的 actions 有一些改變，這裡我們想讓他可以移除特定的按鈕，所以 `Remove` case 現在擁有一個 ID。

```elm
type Action
    = Insert
    | Remove ID
    | Modify ID Counter.Action
```
其中的`update` function 和範例 3的相同。

```elm
update : Action -> Model -> Model
update action model =
  case action of
    Insert ->
      { model |
          counters = ( model.nextID, Counter.init 0 ) :: model.counters,
          nextID = model.nextID + 1
      }

    Remove id ->
      { model |
          counters = List.filter (\(counterID, _) -> counterID /= id) model.counters
      }

    Modify id counterAction ->
      let updateCounter (counterID, counterModel) =
            if counterID == id
                then (counterID, Counter.update counterAction counterModel)
                else (counterID, counterModel)
      in
          { model | counters = List.map updateCounter model.counters }
```

其中的 `Remove`， 我們過濾出了想要的ID


最後是 `view`:

```elm
view : Signal.Address Action -> Model -> Html
view address model =
  let insert = button [ onClick address Insert ] [ text "Add" ]
  in
      div [] (insert :: List.map (viewCounter address) model.counters)

viewCounter : Signal.Address Action -> (ID, Counter.Model) -> Html
viewCounter address (id, model) =
  let context =
        Counter.Context
          (Signal.forwardTo address (Modify id))
          (Signal.forwardTo address (always (Remove id)))
  in
      Counter.viewWithRemoveButton context model
```

在 `viewCounter` function中，我們建造了 `Counter.Context` 用來傳遞所有必要的 forwarding addresses。在兩個情況，我們均標註了 `Counter.Action` 讓我們知道該移除或修改哪個counter、


## Big Lessons So Far(到目前為止)

**Basic Pattern** &mdash; 所有東西都是圍繞著 `Model`所建構的，包含 `更新` model, 以及將model轉為 `view` ，都是根據這個設計模式在變動。

**Nesting Modules** &mdash; Forwarding addresses 讓巢狀化更加簡單，把實做細節整個隱藏起來。 我們可以繼續往下一層深入實做，而每一層只需要知道在他的上一層發生了什麼事就好。

**Adding Context** &mdash; 有時在 `更新` 或是 `檢視` 我們的 model時，額外的資訊是很必要的。我們可以增加一些 `Context`到這些 functions 在避免 `Model`變得更複雜的情況下，將這些資訊傳遞進去。

```elm
update : Context -> Action -> Model -> Model
view : Context' -> Model -> Html
```

在巢狀結構下的每一層， 我們可以導出一些特定的 `Context`給子模組使用。

**Testing is Easy** &mdash; 我們在這建立的所有function都是所謂的 [pure functions][pure].這讓你在測試你的 `update` function時
變得很簡單。 在這之中沒有特定的步驟，你可以直接呼叫你想測試的函式與參數來進行測試。

[pure]: http://en.wikipedia.org/wiki/Pure_function


## Example 5: Random GIF Viewer

**[demo](http://evancz.github.io/elm-architecture-tutorial/examples/5.html) / [see code](examples/5/)**

我們展示了如何建立巢狀的元件， 但，我們該如何執行一個HTTP request呢?如何跟 database 取得資料?在這個範例中使用了 [the `elm-effects` package][fx]來建立一個簡單的元件，可以從 giphy.com取得隨機的 gifs  其中包含 “funny cats” topic。

[fx]: http://package.elm-lang.org/packages/evancz/elm-effects/latest

在這個範例[the implementation](examples/5/RandomGif.elm)，與範例1很類似， `Model` 如下(非常典型)l:

```elm
type alias Model =
    { topic : String
    , gifUrl : String
    }
```

我們需要知道要找尋的 `topic` 以及 `gifUrl`。這個範例特別點在於`init` 與 `update`是一個暫時為空想的types:

```elm
init : String -> (Model, Effects Action)

update : Action -> Model -> (Model, Effects Action)
```

相較於直接返回一個新的 `Model`，為了讓我們可以執行一些效果[the `Effects` API][fx_api]，可參考如下範例

[fx_api]: http://package.elm-lang.org/packages/evancz/elm-effects/latest/Effects

```elm
module Effects where

type Effects a

none : Effects a
  -- don't do anything

task : Task Never a -> Effects a
  -- request a task, do HTTP and database stuff
```

其中的 `Effects` type為一個 擁有許多不同 tasks的資料結構，將會在未來去執行，我們用下面的範例來展示 `update` 是如何執行的:

```elm
type Action
    = RequestMore
    | NewGif (Maybe String)


update : Action -> Model -> (Model, Effects Action)
update msg model =
  case msg of
    RequestMore ->
      ( model
      , getRandomGif model.topic
      )

    NewGif maybeUrl ->
      ( Model model.topic (Maybe.withDefault model.gifUrl maybeUrl)
      , Effects.none
      )

-- getRandomGif : String -> Effects Action
```

使用者可以觸發一個 `RequestMore` action 於點擊“More Please!” 按鈕之後， 當server 回覆時將返回一個 `NewGif` action，這兩個情景都寫在`update` function中。

其中 `RequestMore` 將會先返回一個已存在的 model， 並且我們還使用了 `getRandomGif` function建造了一個 `Effects Action`。 在後面會講到`getRandomGif`是如何定義的。現在我們只需要知道，當`Effects Action` 在執行時，他會產生大量的 `Action` values並且被導向到程式的各個部分。最後 `getRandomGif model.topic` 將產生向下面這樣的action:

```elm
NewGif (Just "http://s3.amazonaws.com/giphygifs/media/ka1aeBvFCSLD2/giphy.gif")
```

並且返回一個`Maybe` 因為這個送往server的request可能會失敗。 `Action`會被傳回 `update` function. 所以假設向server的請求失敗時，我們依然保持原有的 `model.gifUrl`.

在 `init`將會發生相同的事。他定義了一個初始的 model並且使用特定的topic向giphy.com’s API請求 GIF 圖片。

```elm
init : String -> (Model, Effects Action)
init topic =
  ( Model topic "assets/waiting.gif"
  , getRandomGif topic
  )

-- getRandomGif : String -> Effects Action
```

當 random GIF effect 完成時， 他將會產生一個 `Action` 並且導向 `update` function.

> **Note:** 目前為止我們使用了 `StartApp.Simple` module 來源為[the start-app package](http://package.elm-lang.org/packages/evancz/start-app/latest)接著我們需要更新 `StartApp` module. 它可以用來處理更複雜的應用
. It has [a slightly fancier API](http://package.elm-lang.org/packages/evancz/start-app/latest/StartApp)他將可以處理 new `init` 與 `update` types.

其中需要注意的一點是 `getRandomGif` function 用來定義如何取得 random GIF，他使用了 [tasks][] 與 [the `Http` package][http], 下面的範例將會教導如何使用他們:

[tasks]: http://elm-lang.org/guide/reactivity#tasks
[http]: http://package.elm-lang.org/packages/evancz/elm-http/latest

```elm
getRandomGif : String -> Effects Action
getRandomGif topic =
  Http.get decodeImageUrl (randomUrl topic)
    |> Task.toMaybe
    |> Task.map NewGif
    |> Effects.task

-- 第一行創造了一個 HTTP GET request. 他試著
-- 去從  `randomUrl topic`取得JSON 
-- 並且使用 `decodeImageUrl`解析它，下方可以看到他們的定義
--
-- 接著我們使用了 `Task.toMaybe`來抓取任何潛在的錯誤 
-- 並且讓 `NewGif` tag 的結果轉為 `Action`.
-- 最後我們將它轉為 `Effects` value 讓它可以用在接下來的
-- `init` 或是 `update` functions中.


-- 給入一個 topic,與 URL 傳給 giphy API.
randomUrl : String -> String
randomUrl topic =
  Http.url "http://api.giphy.com/v1/gifs/random"
    [ "api_key" => "dc6zaTOxFJmzC"
    , "tag" => topic
    ]


--  JSON decoder 將會接受大批的 JSON 並且
-- 取出其中的 `json.data.image_url` 
decodeImageUrl : Json.Decoder String
decodeImageUrl =
  Json.at ["data", "image_url"] Json.string
```

當我們寫好這些後，未來，我們將可以使用 `getRandomGif` 於 `init`與 `update` functions中

其中有趣的一點是， `getRandomGif`所返回的task將永遠不會失敗，因為我們希望所有可能發生的失敗都要被明確的處理，下面將會解釋這點。

每個`Task` 有兩個型態，分別為 failure type 與 success type。 舉例來說:一個 HTTP task 可能有一個type 類似 `Task Http.Error String`
以此範例來說，它可能會失敗於`Http.Error` 或是成功返回 `String`， 這讓我們可以處理一系列的task並且不用處理錯誤發生。

現在，假設我們有一個 component 要求了一個  task, 但是這個 task 失敗了。接下來會發生什麼事? 誰會被通知? 該如何復原它? 
我們創造了一個發生錯誤時的錯誤型態 `Never` 我們讓任何可能發生的錯誤，都轉到了 success type ，讓他們可以明確地被處理。
在範例中，我們使用了 `Task.toMaybe : Task x a -> Task y (Maybe a)` 所以我們的 `update` function 可以精準的處理 HTTP failures的情況。



## Example 6: Pair of random GIF viewers

**[demo](http://evancz.github.io/elm-architecture-tutorial/examples/6.html) / [see code](examples/6/)**

一般的effects 可以被處理，但如果是*巢狀的* effects呢?這個範例使用了和範例 5同樣的程式，用來建立一對獨立的GIF viewers.

在你看完 [the implementation](examples/6/RandomGifPair.elm)後，你會發現他和範例二有點類似， 其中的 `Model`定義了兩個 `RandomGif.Model` 的值:

```elm
type alias Model =
    { left : RandomGif.Model
    , right : RandomGif.Model
    }
```

這讓我們可以分別的處理它們。 其中的actions指是負責用來傳遞訊息到子組件用的。

```elm
type Action
    = Left RandomGif.Action
    | Right RandomGif.Action
```

我們使用 `Left` 與 `Right` 在我們的 `update` 與 `init` functions中

```elm
-- Effects.map : (a -> b) -> Effects a -> Effects b

update : Action -> Model -> (Model, Effects Action)
update action model =
  case action of
    Left msg ->
      let
        (left, fx) = RandomGif.update msg model.left
      in
        ( Model left model.right
        , Effects.map Left fx
        )

    Right msg ->
      let
        (right, fx) = RandomGif.update msg model.right
      in
        ( Model model.left right
        , Effects.map Right fx
        )
```

在每個分支中，我們使用了 `RandomGif.update` function 其可以回傳一個 model 以及(effect)  `fx`。和先前一樣先回傳一個普通的model，
但我們需要在effects中做一些不同的事。我們這次不讓他直接return，我們將使用 [`Effects.map`](http://package.elm-lang.org/packages/evancz/elm-effects/latest/Effects#map) function
將他們轉為同類型的`Action`，和 `Signal.forwardTo`類似，讓我們對values進行 tag的動作，讓我們清楚的知道它該被導向哪裡。

而`init` function也做一樣的事， 我們提供一個topic 給每個 random GIF viewer 並且得到回傳的初始 model 與 effects。

```elm
init : String -> String -> (Model, Effects Action)
init leftTopic rightTopic =
  let
    (left, leftFx) = RandomGif.init leftTopic
    (right, rightFx) = RandomGif.init rightTopic
  in
    ( Model left right
    , Effects.batch
        [ Effects.map Left leftFx
        , Effects.map Right rightFx
        ]
    )

-- Effects.batch : List (Effects a) -> Effects a
```

在這個範例，我們不止使用 `Effects.map` 來 tag 結果，我們還會使用 [`Effects.batch`](http://package.elm-lang.org/packages/evancz/elm-effects/latest/Effects#batch) function 來讓他們混在一起。
 每個 requested tasks 將會獨立的運行，所以 left 與 right effects將會同一時間一起運作。


## Example 7: List of random GIF viewers

**[demo](http://evancz.github.io/elm-architecture-tutorial/examples/7.html) / [see code](examples/7/)**

這個範例讓你有一系列的 random GIF viewers 你可以創造你自己的topics，並且，我們仍然使用之前的 `RandomGif` module。

當你看完 [the implementation](examples/7/RandomGifList.elm) 你會發現他和 範例 3是相對應的。我們將所有子model放在相同list ，
並用ID來分辨與連結它們， 唯一改變的地方在於:在 `init` 與 `update` function中的 `Effects` ， 將使用 `Effects.map` 與 `Effects.batch`把他們放在一起。


如果你對下面這個章節有任何的問題，你可以在這個repo創造一個issue來解決你的問題。


## Example 8: Animation

**[demo](http://evancz.github.io/elm-architecture-tutorial/examples/8.html) / [see code](examples/8/)**

現在我們知道擁有tasks的 components 可以被巢狀的使用， 但要怎麼把它應用在動畫中呢?

有趣的是， 它的做法和先前的做法類似! 

這個範例是兩個可以點擊的四方體， 當你點擊後， 它會旋轉90度。總體來說這裡的code 源自於 範例 2 和 範例 6 
我們將所有跟動畫相關的邏輯放在`SpinSquare.elm` 我們重複使用的部分放在 `SpinSquarePair.elm`. 

根據這個範例 [in `SpinSquare`](examples/8/SpinSquare.elm) 第一件要做的事為處理 model:

```elm
type alias Model =
    { angle : Float
    , animationState : AnimationState
    }


type alias AnimationState =
    Maybe { prevClockTime : Time,  elapsedTime: Time }


rotateStep = 90
duration = second
```

我們核心的model為 `angle` 指出了四方體的當前角度，而`animationState` 用來指出目前的動畫，假如現在沒有動畫，它將是 `Nothing`
但假如現在有動畫，它將會是:
  
  * `prevClockTime` &mdash; 可以讓我們知道與上次的影格相距多少毫秒(milliseconds) 。
  * `elapsedTime` &mdash;指出 數字0 與 `已經過時間`兩者之差距，用來了解動畫進行了多久。

而`rotateStep` 用來宣告每次點擊他轉了多少角度，你可以隨意去改變它，不會對你程式造成影響。

有趣的事情發生在 `update`中:

```elm
type Action
    = Spin
    | Tick Time


update : Action -> Model -> (Model, Effects Action)
update msg model =
  case msg of
    Spin ->
      case model.animationState of
        Nothing ->
          ( model, Effects.tick Tick )

        Just _ ->
          ( model, Effects.none )

    Tick clockTime ->
      let
        newElapsedTime =
          case model.animationState of
            Nothing ->
              0

            Just {elapsedTime, prevClockTime} ->
              elapsedTime + (clockTime - prevClockTime)
      in
        if newElapsedTime > duration then
          ( { angle = model.angle + rotateStep
            , animationState = Nothing
            }
          , Effects.none
          )
        else
          ( { angle = model.angle
            , animationState = Just { elapsedTime = newElapsedTime, prevClockTime = clockTime }
            }
          , Effects.tick Tick
          )
```

我們需要處理兩種 `Action` :

  - `Spin` 當一個 user 點擊shape並且 requesting a spin。 接著在 `update` function中，假設現在沒有動畫在進行，我們會request 一個 clock tick，並且保持原來的狀態，但假裝已經有事情在作用了。
  - `Tick` 當我們取得了 clock tick 我們將需要取得 animation step.在 `update` function中 ，我們需要去更新 `animationState`. 
  -第一件事，我們會去檢查當下是否有動畫在進行， 假如有，我們會使用當下的 `elapsedTime` 去確認 `newElapsedTime`的值。
並且在其中加入 `time diff`。

假設現在的elapsed time 大於 `duration` 我們將會停止動畫，並且暫停 requesting new clock ticks.
假設小於， 我們會更新現在的 animation state 並且 request another clock tick。



最後，我們會有`view` function! 在這個範例有一個不錯的動畫 ，但其實我們只是以線性的方式去遞增`elapsedTime`。這是如何發生的?

其中 `view` 的程式碼是源自 [`elm-svg`](http://package.elm-lang.org/packages/evancz/elm-svg/latest/) 為了做出其他更有趣並且可點擊產生動畫的形狀. 
在view程式碼中 `toOffset` 將會計算目前所旋轉的偏移量 `AnimationState`.

```elm
-- import Easing exposing (ease, easeOutBounce, float)

toOffset : AnimationState -> Float
toOffset animationState =
  case animationState of
    Nothing ->
      0

    Just {elapsedTime} ->
      ease easeOutBounce float 0 rotateStep duration elapsedTime
```

我們使用的是[@Dandandan](https://github.com/Dandandan)’s [easing package](http://package.elm-lang.org/packages/Dandandan/Easing/latest) 讓我們可以簡單的做到一些動畫 [all sorts of cool easings](http://easings.net/)包含數字,顏色,點,或是任何其他你想要的東西。.

`ease` function 會取得一個數字在 0 與 `duration`間。 接著把它轉換為 0 與 `rotateStep` 間的數字
並且提供一個 easing， 在範例中，我們提供了 `easeOutBounce` 意思為我們slide from 0 to `duration`，我們將會獲得一個數字在 0 and 90 之間，並且具有easing 效果。

接著在下面的連結試試 `easeOutBounce` 吧 [other easings](http://package.elm-lang.org/packages/Dandandan/Easing/latest/Easing)


我們使用 `SpinSquarePair`將大部分的東西結合再一起，但他們其實和範例  2 與範例 6 類似。

以上即是我們使用這個  library所進行的animation ! 如果有任何不清楚的地方請歡迎提出來!

>Note: 我期待我們可以於這個核心概念上做一些更酷的東西 。 如果你有任何更好的想法，請讓我們知道!



#Reactivity

在上一章，我們學習了有關Elm 的架構，於這一章，
我們將談到如何與 servers進行溝通、使用 websockets等等， 下面這張圖展示了一些基本概念

![456](https://cloud.githubusercontent.com/assets/11001914/15096410/be52f858-1528-11e6-846a-b2b53a98f41d.png)


我們程式主要邏輯都在Elm Architecture被描述到了，讓我們可以達到 stateless functions 與 immutability。這裡我們將會談到有關 
signals ，用來對事件進行路由的動作。

當我們想要產生一些effect時，我們會建立一個與核心邏輯分開的service， 每個 service 會負責不同的 task，例如 與資料庫進行連接，或使用
websockets等等，我們將這些都寫在 tasks中。

把這些 services 分開，對我們有很大的幫助，最明顯的幫助是在未來進行測試時會更為簡單。

#Signals

Signals 負責事件的導向，它將會使用到 Elm Architecture。 在前面的 start-app package我們把這些細節隱藏了， 它只是很簡單的在 signals外面包上了一層。

你可以想像 signals 是一個固定在運行的程式網絡，從input收到訊息後將它轉向，最終，把產生的訊息輸出到畫面上。

![485](https://cloud.githubusercontent.com/assets/11001914/15097373/a175170c-154b-11e6-9ad6-cdb3e009f855.png)

上圖是Elm programs中處理程序的流向，我們程式的所有狀態都存在 foldp中，我們主要使用 signals 來進行event的導向。

>Note:你可能會想: “全部的狀態都保存在同個地方?! 那怎麼處理關於 encapsulation的問題呢?!?!” 在你關掉這個 tab之前，你可以想像這就像是 一個管理 database 的人: 管理所有 state最困難的地方在於保持它的一致性。 我們要如何保證在一個元件中所做的改變會正確的傳遞到另一個地方呢? 怎麼知道它所存取的state是最新的呢? 當在你的系統中開始有更多的元件時，這些問題將會變得更加的複雜。 以你以前寫Javascript的經驗中，
state 中的不一致 大概是產生 bugs的最主要原因吧。

在 Elm中 我們把一致性的問題從模組化分開。其中的foldp是一個集中儲存資料的中心，可確保一致性。 而 Elm Architecture 可以保證
我們的程式模組化。把這些概念分開，我們將可以做得更好。

我們使用下圖中的 relatively focused API於 [Signal module API](http://package.elm-lang.org/packages/elm-lang/core/3.0.0/Signal)來建立這個網絡:

```
map : (a -> b) -> Signal a -> Signal b

filter : (a -> Bool) -> a -> Signal a -> Signal a

merge : Signal a -> Signal a -> Signal a

foldp : (a -> s -> s) -> s -> Signal a -> Signal s
```

建議你先看完[signal examples](http://elm-lang.org/examples) 來對這些 API 有基本的概念之後再繼續，我們將會談到如何將這些基本的導向機制轉為可以執行 HTTP requests的services 以及其他更多的功能。

>Note:當你想要寫一個很好的模組化程式時，建議你盡量少用signals ， 而使用普通的 functions與values。假設你未來在使用
signal 時遇到了困難， 你可以問問自己 “我將如何將這些轉為 functions 與 values?”

##Tasks

Tasks 用來描述一些可能會失敗的非同步操作，像是HTTP requests或是對database寫資料等等，許多有關瀏覽器的api在elm中都稱為tasks

* [elm-http](http://package.elm-lang.org/packages/evancz/elm-http/3.0.0/) —  servers 操作
* [elm-history](https://github.com/TheSeamau5/elm-history/) — 改變 browser history
* [elm-storage](https://github.com/TheSeamau5/elm-storage/) — 本地存儲

Tasks 類似輕量化的 threads ， 所以你可以有一系列的 tasks 同時運行， 並且在他們任何一個發生中斷時跳過它。

這個範例將會使用 elm-http package 來建立一個常見的 HTTP requests程式， 像是 [zip codes](http://elm-lang.org/examples/zip-codes) 
以及 [querying flickr](http://elm-lang.org/examples/flickr) 其中的API比 XMLHttpRequest 還要好用，
並且比 JavaScript’s promises有更好的錯誤處理。 

開始之前，請先安裝  evancz/task-tutorial package 並在你的資料夾中執行下面的 command:

```
elm-package install evancz/task-tutorial -y
elm-package install evancz/elm-html -y
elm-package install evancz/elm-http -y
elm-package install evancz/elm-markdown -y
```

使用[ TaskTutorial](http://package.elm-lang.org/packages/evancz/task-tutorial/1.0.3/TaskTutorial)，可以幫我們建立一些基本的功能

####Basic Example

下面是一個簡單的 function 可以印出值到 console 中:

```
print : a -> Task x ()
```

我們給予 print function 一個 value， 它將返回一個 Task 它可以在未來被執行，並印出這個value ， 其中的x 用來顯示錯誤發生的類型,
我們現在先不用關注它，之後會再講到。

為了真正執行一個 task，我們將它轉向到 [port](http://elm-lang.org/guide/interop) 將ports想像成 是你可以要求elm runtime為你做的一些事。
在這裡 ，它的意思為執行這個 task.下面的範例中將  print和 ports 放在一起，用來每秒印出現在的時間。

```
import Graphics.Element exposing (show)
import Task exposing (Task)
import TaskTutorial exposing (print)
import Time exposing (second, Time)


-- A signal that updates to the current time every second
clock : Signal Time
clock =
  Time.every second


-- Turn the clock into a signal of tasks
printTasks : Signal (Task x ())
printTasks =
  Signal.map print clock


-- Actually perform all those tasks
port runner : Signal (Task x ())
port runner =
  printTasks


main =
  show "Open your browser's Developer Console."
```
當初始化這個 module時，我們將會發現每秒將會印出現在的時間，printTasks signal 創造了許多 tasks， 但是這並沒有對他自己做任何事
。就像是在現實生活中，創造 task 不代表task真的有發生。我可以在代辦事項寫上許多的 “買更多牛奶” ，但我仍然需要動身去超市買，否則它將不會自動出現在我的冰箱。

在Elm中的 tasks 在我們將他轉交給 port 之前他並不會去真正執行。 不像是 JavaScript中的 callback，elm的 runtime 僅僅只是執行了這個 task。

我們可以傳給port 一個 task 或是一個 signal 帶有許多 tasks。 當你給的是 signal時，所有的 tasks將會被執行，原因是為了避免 overlapping。

####Chaining Tasks

在上面的範例中，我們使用了[print](http://package.elm-lang.org/packages/evancz/task-tutorial/1.0.3/TaskTutorial#print)
但如果我們想要執行更加複雜的task呢? 參考以下的步驟:

首先介紹 [getCurrentTime](http://package.elm-lang.org/packages/evancz/task-tutorial/1.0.3/TaskTutorial#getCurrentTime)它可以比 print做更多的事情!

```
getCurrentTime : Task x Time
```

這是一個單純給你現在時間的 task，當你執行它時， 它會告訴你現在是幾點，現在我們要做的是執行 `getCurrentTime`並且執行 `print`
先讓我們看一下完整版的樣子，在一一去做介紹:

```
import Graphics.Element exposing (show)
import Task exposing (Task, andThen)
import TaskTutorial exposing (getCurrentTime, print)


port runner : Task x ()
port runner =
  getCurrentTime `andThen` print


main =
  show "Open the Developer Console of your browser."
```
首先， 注意到其中伊個不常用的反引號，它可以將普通的function轉為 infix operators。 和其他範例相同， (add 3 4) 與 (3 `add` 4)同樣意思。

所以(getCurrentTime `andThen` print) 與 (andThen getCurrentTime print)為相同意思。 當使用反引號時，它讓我們閱讀起來更像是一般英文的用法。

現在我們知道andThen 是一個普通的 function 並且擁有兩個參數，讓我們看一下它的型別:

```
andThen : Task x a -> (a -> Task x b) -> Task x b
```

第一個參數是我們想要執行的Task，即為getCurrentTime。第二個參數是一個 callback用來建造一個新的 task。
(在這裡的意思為將現在的時間印出來)

看一下下面稍為詳細的 task chain將對你有幫助:

```
printTime : Task x ()
printTime =
  getCurrentTime `andThen` print


printTimeVerbose : Task x ()
printTimeVerbose =
  getCurrentTime `andThen` \time -> print time
```

這兩個的意思相同，但是第二個比較明確的指出:我們在等待一個時間，並且將他印出

其中的andThen function 在使用 tasks 很重要，它讓我們可以創造複雜的Task chains
接下來的範例它將會很常見

####Communicating with Mailboxes
我們現在執行了 tasks但把結果丟掉。但假如我們想從 server取得一些資訊並用到我們的程式中呢?
我們可以使用 [Mailbox](http://package.elm-lang.org/packages/elm-lang/core/3.0.0/Signal#Mailbox)
就像是我們在建構 UIs 並希望他回傳值時一樣 ，下面是在 [Signal module](http://package.elm-lang.org/packages/elm-lang/core/3.0.0/Signal)中的一些定義:

```
type alias Mailbox a =
    { address : Address a
    , signal : Signal a
    }

mailbox : a -> Mailbox a
```

 mailbox 擁有兩個鍵值對: (1)  一個address 用來傳遞訊息(2)一個 signal 當我們收到訊息時更新它。當我們建立需要提供一個初始值
給Signal.

在這裡的send function 是傳送訊息給 mailbox主要的方式

```
send : Address a -> a -> Task x ()
```

你提供一個address與 value，當 task 被執行時， value 會出現在相應的 mailbox。
就像是真實的信箱，接著看一下，下面的範例:

```
import Graphics.Element exposing (Element, show)
import Task exposing (Task, andThen)
import TaskTutorial exposing (getCurrentTime, print)


main : Signal Element
main =
  Signal.map show contentMailbox.signal


contentMailbox : Signal.Mailbox String
contentMailbox =
  Signal.mailbox ""


port updateContent : Task x ()
port updateContent =
  Signal.send contentMailbox.address "hello!"
```
程式一開始只顯是一個空的字串，其為在 mailbox中的初始值，接著我們立刻執行 updateContent task 
它送出了訊息到contentMailbox。當他抵達時，contentMailbox.signal 的值進行了更新，接著畫面顯示了 "hello!" 。


現在，我們對andThen 與 Mailbox 有了進一步的了解，接著讓我們看一些更實用的範例!

####HTTP Tasks


我們在web app 使用中最常做的事就是與servers做溝通，  elm-http library 提供了大部分你所需要的函式，
下面先來介紹有關 Http.getString function

```
Http.getString : String -> Task Http.Error String
```

我們提供一個 URL，它會創造一個 task 用來取得一些資源，最後 x 會是 error type! 這個 task 有可能會產生 Http.Error 或是 succeed且產生一個 String.

下面的函式用來載入 在e Elm Package Catalog中的README packages

```
import Http
import Markdown
import Html exposing (Html)
import Task exposing (Task, andThen)


main : Signal Html
main =
  Signal.map Markdown.toHtml readme.signal


-- set up mailbox
--   the signal is piped directly to main
--   the address lets us update the signal
readme : Signal.Mailbox String
readme =
  Signal.mailbox ""


-- send some markdown to our readme mailbox
report : String -> Task x ()
report markdown =
  Signal.send readme.address markdown


-- get the readme *and then* send the result to our mailbox
port fetchReadme : Task Http.Error ()
port fetchReadme =
  Http.getString readmeUrl `andThen` report


-- the URL of the README.md that we desire
readmeUrl : String
readmeUrl =
  "https://raw.githubusercontent.com/elm-lang/core/master/README.md"
```

有趣的部分發生在 fetchReadme port。 我們嘗試從 readmeUrl取得資源，假如成功了，我們將他轉送到 readme mailbox。 假如失敗，則沒有任何訊息會送出。
假如server 收到了 README 的回覆，我們會看到畫面從空白轉為 elm-lang/core readme中的內容!

####More Chaining

我們已經看到 andThen 用來將兩個 tasks 連接在一起，但我們要如何連接更多的 tasks呢?最終，這將會看起來有點奇怪， 所以你可以使用一些
indentation 的方式，讓它看起來好一點。 讓我們看下面的範例是如何做到的:

```
import Graphics.Element exposing (show)
import Task exposing (Task, andThen, succeed)
import TaskTutorial exposing (getCurrentTime, print)
import Time exposing (Time)


getDuration : Task x Time
getDuration =
  getCurrentTime
    `andThen` \start -> succeed (fibonacci 20)
    `andThen` \fib -> getCurrentTime
    `andThen` \end -> succeed (end - start)


fibonacci : Int -> Int
fibonacci n =
  if n <= 2 then
    1
  else
    fibonacci (n-1) + fibonacci (n-2)


port runner : Task x ()
port runner =
  getDuration `andThen` print


main =
  show "Open the Developer Console of your browser."
```
這看起來很自然，取得現在的時間，並且執行 fibonacci function，之後再次取得現在的時間，最後傳回開始與結束時間的差距。

你可能會有疑問: “why is start in scope two tasks later?” 原因是，這裡的箭頭是一個匿名函式， 所以假如我們把括號放再 getDuration function，它將會看起來像這樣:

```
getDuration : Task x Time
getDuration =
  getCurrentTime
    `andThen` (\start -> succeed (fibonacci 20)
    `andThen` (\fib -> getCurrentTime
    `andThen` (\end -> succeed (end - start))))
```
現在你可以看到我們之前講的 indentation奇怪的地方! 你將會常看到這種鏈式的設計模式， 因為它可以保存許多變數在同一個範圍內，
讓許多 tasks使用。

####錯誤處理(Error Handling)

到目前為止我們只在乎成功的task，但如果HTTP request 返回的是一個 404或是一個不能被解析的 JSON 格式呢? 
我們有兩種主要的方式可以處理這種類型的 tasks所發生的錯誤，第一種是使用 onError function:

```
onError : Task x a -> (x -> Task y a) -> Task y a
```

這看起來跟 andThen很類似，但他只有在發生錯誤時才會被觸發， 所以假如我們想從一個錯誤的 JSON request回復時,我們可以這樣寫:

```
import Graphics.Element exposing (show)
import Http
import Json.Decode as Json
import Task exposing (Task, andThen, onError, succeed)
import TaskTutorial exposing (print)


get : Task Http.Error (List String)
get =
  Http.get (Json.list Json.string) "http://example.com/hat-list.json"


safeGet : Task x (List String)
safeGet =
  get `onError` (\err -> succeed [])


port runner : Task x ()
port runner =
  safeGet `andThen` print


main =
  show "Open the Developer Console of your browser."
```
有了這個 get task，雖然我們可能產生 Http.Error的錯誤，但當我們加入了 recovery with onError最後我們仍然可以執行 safeGet task 

當一個 task 永遠會被成功的執行時，  牽制  error type是不可能的， 因為type 可能是任何類型，我們永遠不會知道，因為他從來不會發生，
這就是為什麼我們要用一個可以是任意型別的 x 於 safeGet中。

第二種錯誤處理的方式為使用 Task.toMaybe 與 Task.toResult

```
toMaybe : Task x a -> Task y (Maybe a)
toMaybe task =
  Task.map Just task `onError` \_ -> succeed Nothing


toResult : Task x a -> Task y (Result x a)
toResult task =
  Task.map Ok task `onError` \msg -> succeed (Err msg)
```
實質上這是把所有錯誤轉為一個success case， 讓我們看下面這個範例

```
import Graphics.Element exposing (show)
import Http
import Json.Decode as Json
import Task exposing (Task, andThen, toResult)
import TaskTutorial exposing (print)


get : Task Http.Error (List String)
get =
  Http.get (Json.list Json.string) "http://example.com/hat-list.json"


safeGet : Task x (Result Http.Error (List String))
safeGet =
  Task.toResult get


port runner : Task x ()
port runner =
  safeGet `andThen` print


main =
  show "Open the Developer Console of your browser."
```

使用了 safeGet 我們可以根據 Result type來處理錯誤，當你再處理一些特定的API實，它們將十分有用。

####進階閱讀(Further Learning)

現在我們對於andThen的鏈式tasks以及錯誤處理有了基本的概念，接著你可以試著閱讀下面這兩個範例:

* [zip codes](http://elm-lang.org/examples/zip-codes)
* [flickr](http://elm-lang.org/examples/flickr)



#Interop

這一章節主要在講如何將 Elm 的程式嵌入到 HTML 中，以及如何與 JavaScript進行溝通。

##HTML Embedding

Elm 可以直接被嵌入一個 <div>標籤中，這讓你可以輕鬆的把 Elm程式與其他 JS project做整合。可以參考下面的範例:

假設我們有一個簡單的程式 [Stamper.elm](https://gist.github.com/evancz/8456627#file-stamper-elm) 
讓你在點擊滑鼠時於畫面上留下一個[圖形](http://elm-lang.org/examples/stamps)

使用下面的指令編譯它:
```
elm-make Stamper.elm
```
將會產生一個名為 elm.js的檔案。 這個 JS 檔案包含了所有嵌入到HTML所需要的要素。

在EmbeddedElm.html檔案中，我們於`<body>` 標籤下方增加一個，`<script>`標籤 並含有以下的程式碼:

```
// get an empty <div>
var div = document.getElementById('stamper');

// embed our Elm program in that <div>
Elm.embed(Elm.Stamper, div);
```
Elm.embed function 需要兩個參數 :

1.一個 Elm module，並且所有名字的最前面都包含的Elm字樣，來避免命名空間汙染，所以原來的Stamper模組變為Elm.Stamper。

2.一個<div>標嵌用來包住我們要嵌入的程式

這樣就夠了!

需要注意的是 Window.dimensions 以及 Mouse.position 作用範圍只有在該 <div>中，沒有包含到整個頁面。
這代表 Stamper中的程式仍然會填滿整個 <div> 並且當你點擊時給予回應。

####另一種嵌入Elm程式的方式(Other ways to embed Elm

下面這個範例將程式嵌入<div>中，但它仍然可以在全螢幕中創造 Elm 元件 ，而另外一個是完全沒有圖形的:

```
// fullscreen version of Stamper
Elm.fullscreen(Elm.Stamper);

// Stamper with no graphics
Elm.worker(Elm.Stamper);
```

在你指定了HTML的輸出檔案後，你也可以讓他自動去產生 HTML
```
elm-make Stamper.elm --output=Main.html
```

##Ports

Ports 是常見的與 JavaScript溝通的方式，讓你可以方便的傳遞訊息，所以你可以在你隨時想要的時候使用 JavaScript。

你可以參考這個[範例](https://github.com/evancz/elm-html-and-js) 
與這個[範例](https://gist.github.com/evancz/8521339) 
在這個文件中將講解你可以使用ports做哪些事情。

####From JavaScript to Elm

當你想要從JavaScript 送訊息到 Elm， 你可以如下使用incoming port :

```
port addUser : Signal (String, UserRecord)
```

我們有一個signal 在 Elm中，名為 addUser 它將會被 JavaScript的某些程式更新。為了送訊息到這個 port
我們需要寫一些如下的東西到 JavaScript中:
```
myapp.ports.addUser.send([
    "Tom",
    { age: 32, job: "lumberjack" }
]);

myapp.ports.addUser.send([
    "Sue",
    { age: 37, job: "accountant" }
]);
```
這將會傳送兩個更新訊息給Elm，並自動轉為值。

##From Elm to JavaScript

從 Elm 送訊息到 JavaScript，你可以如下定義一個 outgoing port :

```
port requestUser : Signal String
port requestUser =
    signalOfUsersWeWantMoreInfoOn
```

在這個範例，我們使用了一個Elm中的 signal並將它的每個值傳送到 JavaScript。 在 JavaScript 這邊，為了處理這些傳來的訊息我們訂閱了這個 port:
```
myapp.ports.requestUser.subscribe(databaseLookup);

function databaseLookup(user) {
    var userInfo = database.lookup(user);
    myapp.ports.addUser.send(user, userInfo);
}
```
我們訂閱了 requestUser port 並且會對 database 進行存取， 當我們取得回傳值時，我們將它傳遞到 Elm中，並且使用另一個 port。
有時你可能會需要對一個  port取消訂閱，如同以下範例:
```
myapp.ports.requestUser.unsubscribe(databaseLookup);
```

你可以查看這兩個範例
https://github.com/evancz/elm-html-and-js
https://gist.github.com/evancz/8521339

##Customs and Border Protection

你需要注意傳送給Ports的值， Elm 是一種靜態語言，所以每個 port 都擁有 border protection用來避免 type errors 
 Ports 也做了一些資料轉換， 讓你在 Elm 與 JS間有很好的資料結構。
 
 可以傳送給 ports 的資料型態是很有彈性的，包含所有有效的 [JSON](http://www.json.org/) 值，與以下所列的 Elm 型態:
 
Booleans and Strings – 在 Elm and JS都適用!

Numbers – Elm ints and floats correspond to JS numbers

Lists – 對應到 JS arrays

Arrays – 對應到 JS arrays

Tuples – 對應到 fixed-length, mixed-type JS arrays

Records – 對應到 JavaScript objects

Signals – 對應到 event streams in JS

Maybes – Nothing and Just 42 correspond to null and 42 in JS

Json – [Json.Encode.Value](http://package.elm-lang.org/packages/elm-lang/core/3.0.0/Json-Encode#Value) corresponds to arbitrary JSON

每個轉換都必須是對稱且為正確的資料型態，假如是一個錯誤的型態，它將會立即於 JS 拋出一個錯誤。
有了border check 之後， Elm 將可以保證你不會遇到任何執行時所產生的 type errors。
