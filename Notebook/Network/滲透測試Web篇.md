# 滲透測試Web篇

## SQL Injection
- 網頁應用程式接受傳遞的參數當中，輸入的參數存在SQL語法，影響了原本預期執行的指令
- 可以利用參數化查詢或是黑名單、白名單，檢查驗證輸入的參數內容

## XSS
- 網頁應用程式未確實將輸入的JavaScript語法過濾與編碼
- 瀏覽器將此JS語法執行。驗證參數輸入的內容，將輸出的內容進行HTML編碼

## CSRF
- 跨站請求偽造
- 流程:
    1. User 訪問並登入 A 網站
    2. User 獲得 Cookie 並存至 User 瀏覽器
    3. User 在未登出 A 網站的情況下瀏覽 B 網站
    4. Hacker 以 B 網站的 Domain 以 A 網站給 User 的 Cookie 對 A 網站發送請求，如果 A 網站沒發現的話就 GG 了。
- 利用CSRF Token來防禦

## Clickjacking
- 點擊劫持技術
- 將iframe設為透明，然後使用者在該網頁上進行操作時，當使用者在要點擊釣魚的按鈕時，其實是點到透明的iframe內容

## SSRF
- Server-side request forgery
- 伺服器端應用程式向攻擊者選擇的任意網域發出HTTP請求

## Nmap
- 預設情況下會去掃描"常見的"1000個Port
- Pn參數，則不會針對這個主機進行Host Discovery(也就是去偵測這台主機是否有存活在線上)
- F表示只掃描常見的100個Port
- 發現開啟了一個Port，先看是甚麼Port或服務，可以使用相對應的工具連線確認看看

## SSH 攻擊
1. 列舉/暴力破解帳號密碼
2. 看版本找有無存在已知的CVE漏洞
3. 看是否有弱加密
4. 如果有其他找到私鑰洩漏，可以嘗試利用key連線過去

## FTP 攻擊
1. 列舉/暴力破解帳號密碼
2. 看版本找有無存在已知的CVE漏洞
3. 看是否有弱加密
4. anoymouns登入

## DNS 攻擊
1. ZONE TRANSFER
2. Dos
3. BIND版本是否過舊

## LDAP
1. 是否有開啟LDAP匿名查詢

## SMTP
1. 是否有帳號列舉風險
2. SMTP Mail Relay

## SQL Server
1. 預設帳密登入 (su)
2. SQL Server弱加密

## SMB
1. 版本查詢
2. 匿名登入
3. 看有沒有磁碟可列舉或mount
