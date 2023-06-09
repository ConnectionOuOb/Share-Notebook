phpMyAdmin 設定方式
===

安裝
---

1. 開啟要設定的電腦的 Terminal
2. 用有管理權限的帳號確認 http 正在執行
    1. 用 ```sudo systemctl status httpd``` 確認是否 runnung
    2. 如果沒安裝
        1. 用 ```sudo yum install httpd -y``` 安裝
        2. 在防火牆上允許通過 ```sudo firewall-cmd --add-service=http --permanent```
        3. ```sudo firewall-cmd --reload``` 重啟防火牆套用設定
    3. 如果沒執行，用 ```sudo systemctl start httpd``` 開啟
3. 用有管理權限的帳號安裝 php ```sudo yum install php -y```
4. 重啟 httpd ```sudo systemctl restart httpd```
5. 新增 EPEL repo ```sudo yum install epel-release -y```
6. 安裝 phpMyAdmin ```sudo yum install phpmyadmin -y```
7. 安裝完成

設定
---

1. 編輯設定檔 ```sudo vim /etc/httpd/conf.d/phpMyAdmin.conf```
2. 會有一行是註解起來的 ```#Port 22```，改成 ```Port {你要設定的PORT}```
    - 例如要改成用 TCP Port 66666 連線，就改成 ```Port 66666```
3. 有一行是 ```#PermitRootLogin yes```，是指可以用 root 最高權限登入系統，建議關閉
    - 該行修改成 ```PermitRootLogin no```
5. 按 **esc**，然後輸入 ```:wq``` 儲存後離開
6. 設定完成


啟用防火牆
---

1. 要開啟 SSH 外部連入要把防火牆開洞
    - 如果為預設的 Port 22 : ```sudo firewall-cmd --permanent --zone=public --add-port=22/tcp```
    - 如果有修改 Port : ```sudo firewall-cmd --permanent --zone=public --add-port={修改的Port}/tcp```
        - 以 Port 66666 為例需輸入 : ```sudo firewall-cmd --permanent --zone=public --add-port=66666/tcp```
2. 重啟防火牆讓設定生效
    - 輸入 ```sudo firewall-cmd --reload```
3. 這樣就能從外部連進來了
