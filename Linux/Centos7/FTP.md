FTP 設定方式
===

安裝
---

1. 開啟要設定的電腦的 Terminal
2. 用有管理權限的帳號執行 ```sudo yum -y install vsftpd```
3. 安裝完成

設定
---

1. 編輯設定檔 ```sudo vim /etc/vsftpd/vsftpd.conf```
2. 可以修改的選項，沒有就新增在檔案尾端 :
    1. 連接上來的 Port (預設21)
        - ```listen_port={要連接的Port}```
        - 以 Port 21111 為例，就修改成 ```listen_port=21111```
    2. 連接上來的 Data port (預設20)
        - ```ftp_data_port={要連接的Port}```
        - 以 Port 21110 為例，就修改成 ```ftp_data_port=21110```
    3. 匿名登入，建議關閉
        - ```anonymous_enable=NO```
    4. 連線數量限制，建議設定
        - ```max_clients=30```
    4. 同一個 IP 連線數量限制，建議設定
        - ```max_per_ip=3```
3. 按 **esc**，然後輸入 ```:wq``` 儲存後離開
4. 設定完成

服務控制
---

1. 開啟 FTP 服務
    - 時機 : FTP 是關閉的時候
    - ```sudo systemctl start vsftpd```
2. 重啟 FTP 服務
    - 時機 : 剛設定完 FTP，要載入設定
    -  ```sudo systemctl restart vsftpd```
3. 關閉 FTP 服務
    - 時機 : FTP 出事情，要緊急關閉的時候
    -  ```sudo systemctl stop vsftpd```
4. 查看 FTP 狀態
    -  ```sudo systemctl status vsftpd```
5. 開機自行啟動 FTP
    - ```sudo systemctl enable vsftpd```

啟用防火牆
---

1. 要開啟 FTP 外部連入要把防火牆開洞
    - 如果為預設的 Port 21 :
        - ```sudo firewall-cmd --permanent --zone=public --add-service=ftp```
        - ```sudo firewall-cmd --permanent --zone=public --add-port=21/tcp```
    - 如果有修改 Port : ```sudo firewall-cmd --permanent --zone=public --add-port={修改的Port}/tcp```
        - 以 Port 21111 為例需輸入 : ```sudo firewall-cmd --permanent --zone=public --add-port=21111/tcp```
2. 重啟防火牆讓設定生效
    - 輸入 ```sudo firewall-cmd --reload```
3. 這樣就能從外部連進來了
