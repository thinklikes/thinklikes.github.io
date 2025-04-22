+++
lastmod = '2025-04-21T11:43:53+08:00'
date = '2025-04-18T11:43:53+08:00'
draft = false
title = 'Golang 新手村(1)'
tags = ['golang']
categories = ['golang 新手村']
+++

## 前言
各位勇者，歡迎降臨 Golang 新手村！你是不是渴望著操控程式之力？這裡就是你的起點，讓我們一同修煉 Go 能力吧！

{{< admonition type=tip title="Tips" open=true >}}
這個系列的文章將會引用官網中 <<A Tour of Go>> 一系列的範例程式。  
出處：
{{< link href="https://go.dev/tour/list" content="A Tour of Go" title="A Tour of Go" >}}


{{< /admonition>}}

## 新手村使用說明
1. 所有的教學任務會以一個新手的觀點來撰寫，從最基本的語法開始介紹，並且附上範例程式碼。
2. 範例程式碼大部分官網取得並僅止於引用，可從連結進入原始網頁中，按下`Run`按鈕測試。
ˇ範例程式碼若有附註，會使用下列幾種區塊來說明：

    {{< admonition type=tip title="Tips" open=true >}}
    
用於提供一些建議或備註的區塊，讓使用者可以更加了解程式碼的使用方式或注意事項。
    
    {{< /admonition>}}

    {{< admonition type=warning title="Warnings" open=true >}}

用於告知有可能會引發錯誤或需要特別注意的區塊，讓使用者可以更加小心地使用。

    {{< /admonition>}}

   {{< admonition type=question title="Questions" open=true >}}

用於提供一些問題或疑問的區塊，讓使用者可以思考或討論。

   {{< /admonition>}}

---

## 拿出你的鍵盤吧！
冒險者們，你不會這樣就慌張了吧？作為一位初心者，首先要做的是保持冷靜，先不要慌。

想像著我們轉生前就讀國小一年級時，看到課本上一大坨文字難免會慌張。而這時老師帶著我們一個字一個字讀完，並且講解文字的意思，我們就是用這樣的方式開始熟悉文字。

經過約十來年的訓練，我們才能夠毫不費力地閱讀文章。閱讀程式語言也是需要透過密集的練習才能夠熟悉的。  

---
首先打開 <<A Tour of Go>> 的[第一個範例](https://go.dev/tour/basics/1)。這個範例主要說的是 Golang 的基本語法，讓我們來看看這段程式碼：
```golang
package main

import "fmt"

func main() {
	fmt.Println("Hello, 世界")
}
```
#### 說明
```golang
package main
```
Golang 開發規範中， `package main` 這一句宣告語句須放在第一行，代表當前的檔案屬於 `main` package。  
package 是一種組成程式碼的方式，把相關的函式、變數和資源組織在一起，以保持程式碼的整潔。  
你可以想像成一個資料夾，裡面放著許多相關的檔案。

---

```golang
import "fmt"
```
目前的程式中引用了 `fmt` package，這是一個內建的 package，在這裡我們用來印出指定的文字。

----
```golang
func main() {
	fmt.Println("Hello, 世界")
}
```
`func main()` 是目前這個程式的主函式，這是程式的進入點。意即執行該檔案時，會預設執行這個函式中的程式碼。
`fmt.Println("Hello, 世界")` 是用來印出文字的指令，這裡我們印出了 `Hello, 世界` 這段文字。

## 小結
冒險者們！幹得不錯，你已經通過了第一項考驗了！相信你已經開始熟悉 Golang 程式碼區塊是怎麼分佈的了，是不是已經隱隱約約知道怎麼操控 Golang 之力了呢？
想要細細品味其中原理，那就往下一個任務前進吧！
