# Web 基礎

## HTTP與HTTPS有甚麼差異
- HTTP是WEB傳輸訊息的協定，內容為明文
- HTTPS則為HTTP的明文內容利用SSL/TLS加密過後的協定

## HTTP是Stateless還是Stateful
stateless無狀態的。每個請求之間為相互獨立。

## HTML/CSS/JavaScript差別
- HTML描述了這個網站的節點元素架構
- CSS則可以調整元素的顯示外觀
- JavaScript則是可以動態執行操作的腳本語言

## 前端跟後端有甚麼區別
- 前端是直接面對客戶端的，會傳送到瀏覽器顯示，使用者可以從瀏覽器看到的內容，通常前端使用HTML/CSS/JavaScript
- 後端則是於伺服器處理，例如一些功能與資料儲存等等，這些後端語言與處理的流程，是無法從客戶端所看到或是顯示的。

## cookie當中的httponly與secure屬性有甚麼用途？
- httponly若設定，則JavaScript無法針對這個Cookie進行操作，用來防禦XSS的
- Secure屬性若設定，則此cookie無法在HTTP當中傳輸，只能在HTTPS當中傳輸，是為了避免HTTP明文傳輸的過程當中，造成cookie的資訊洩漏

## 同源政策(SOP)
- 網域之間資源存取的限制規則
- 協定、Domain、Port，三者要相同

## HTTP 方法
- GET/POST/HAED/OPTIONS/TRACE/DELETE/PUT/CONNECT

## HTTP 狀態碼
- 200 OK表示正常回應
- 301與302為轉址回應
- 403是表示沒有存取該資源的權限
- 404表示找不到資源
- 500表示伺服器錯誤

## Security Header
- 加上之後，可以相對應執行一些防禦機制的Header

## CORS
- 跨源資源共享。可以在 HTTP 標頭中指定允許的來源。發送帶有選項設定的預檢請求，詢問伺服器是否批准，如果伺服器批准，則發送實際請求

## SSL handshake
- ![alt text](image/SSL.png)
