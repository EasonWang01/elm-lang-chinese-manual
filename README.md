# elm-lang 的中文手冊 

翻譯自  

https://github.com/elm-lang/elm-compiler

#目錄

1.[安裝](#安裝)

2.[開始使用](#開始使用)



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

#開始使用

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

