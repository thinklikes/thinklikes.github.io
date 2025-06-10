---
title: "我在現實生活中用 n8n 開外掛(2) - 手動觸發器 Trigger Manually"
date: 2025-06-10
draft: false
tags: [ 'n8n', '自動化', 'Triggers' ]
topics: [ "我在現實生活中用 n8n 開外掛" ]
---

## 節點名稱

手動觸發器 `Trigger Manually`，是手動啟動工作流程的節點，通常用於測試或開發階段。我們也可以輸入一些數據當作假資料或是初始資料，作為工作流程的輸入。
{{< figure src="trigger_manually.png" caption="手動觸發器 `Trigger Manually`" >}}

當模板中有手動觸發器節點時，模板上會出現`Test workflow`按鈕。按下`Test workflow`按鈕，即可執行這個工作流程。

## 加入節點

1. 新建立一個工作流程後，點擊畫布上的`Add first step...`按鈕，在右側欄上找到`Trigger Manually`節點。或是在畫布上工作時，按下鍵盤上的
   `tab`按鍵，即可呼叫出右側欄，並在右側欄上搜尋`Trigger Manually`節點。
2. 點擊或拖曳節點到畫布上即可。

## 輸入

`Trigger Manually`並不需要任何的輸入值。

## 輸出

`Trigger Manually`預設沒有任何輸出值，但我們可以放一些假資料做為初始資料。

### **輸出時使用假資料**

1. 在`Trigger Manually`上用滑鼠左鍵點兩下，即可檢視節點詳細資料。
2. 在`OUTPUT`區域中，點擊`set mock data`或右上角的編輯按鈕，開啟`OUTPUT`編輯視窗。
3. 這時編輯框中已經填入了一些資料，但我們依然可以填入一些自訂的資料。這些資料會在工作流程執行時作為輸入值傳遞給下一個節點。

## 使用範例

### **手動觸發寄信**

在這個範例中，我們將使用 `Trigger Manually` 節點來手動觸發一個寄信的工作流程。
需要準備一個`SMTP server`的連線資訊，來為我們寄信。以下的範例中我們使用`Gmail SMTP server`。

{{< alert "circle-info" >}}
第一次使用`Gmail SMTP server`，請先按照這些步驟設定：

1. 確認您的`Google`帳戶已啟用[兩步驟驗證](https://support.google.com/accounts/answer/185839)。
2. 建立[應用程式密碼](https://support.google.com/accounts/answer/185833)。
{{< /alert >}}

步驟如下：

1. 按下`tab`按鈕，搜尋並選擇 `Trigger Manually`節點。
2. 在 `Trigger Manually` 中設定一些假資料，例如：
   ```json
   [
     {
       "email": "<test email address>",
       "subject": "Test Email",
       "body": "This is a test email sent from n8n."
     }
   ]
   ```
3. 在`Trigger Manually`節點右側的`+`點一下，搜尋並選擇`Send Email`節點，系統會自動要求輸入參數。
4. 在中間版面中，`parameters`的`Credential to connect with`欄位中選擇`Create new credentials`。
   {{< figure src="create_new_credentials.png">}}
5. 在彈出的視窗中輸入`SMTP server`連線資訊，輸入完成後點擊`Save`按鈕，系統會自動為我們測試連線。
   - User: 輸入您的 Gmail 信箱
   - Password: 輸入剛剛建立的應用程式密碼
   - Host: smtp.gmail.com
   - Port: 465

   {{< figure src="smtp_connection.png">}}
6. 回到`parameters`，輸入其他欄位資料：
   - From Email: 信件上顯示的寄件人，例如：Nathan Doe \<nate@n8n.io\>
   - To Email: 收件人，例如：Jane Doe \<jane@n8n.io\>
   - Subject: 信件主旨
   - Email Format: 信件本文的格式，我們先使用 `Text`。
   - Text: 信件本文  
  
   上述資料也可以使用表達式來引用 `Trigger Manually` 節點的輸出資料，如下圖操作：
   {{< figure src="email_info.png">}}

7. 完成後點擊上方的`Test step` 按鈕，可單獨執行該節點，執行成功的話，`OUTPUT`版面會返回寄信的相關`meta`資料，其中的`response`欄位會有`OK`的文字。
   {{< figure src="send_successfully.png">}}
8. 接著就可以去收信看看了。

## 小結
在這篇文章中我們介紹了 `n8n` 中的手動觸發器節點 `Trigger Manually`，並展示了如何使用它來手動啟動工作流程，另外我們也提到了使用`Send email`節點來寄信，這些操作是不是讓你更加認識了`n8n`的魔法了呢？。