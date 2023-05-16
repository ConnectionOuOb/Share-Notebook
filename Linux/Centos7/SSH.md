SSH 設定方式
===

安裝
---

1. 開啟要設定的電腦的 Terminal
2. 用有管理權限的帳號執行 ```sudo yum -y install openssh openssh-server```
3. 安裝完成

設定
---

1. 編輯設定檔 ```sudo vim /etc/ssh/sshd_config```
2. 會有一行是註解起來的 ```#Port 22```，改成 ```Port {你要設定的PORT}```
    - 例如要改成用 TCP Port 66666 連線，就改成 ```Port 66666```
3. 有一行是 ```#PermitRootLogin yes```，是指可以用 root 最高權限登入系統，建議關閉
    - 該行修改成 ```PermitRootLogin no```
5. 按 **esc**，然後輸入 ```:wq``` 儲存後離開
6. 設定完成

服務控制
---

1. 開啟 SSH 服務
    - 時機 : SSH 是關閉的時候
    - ```sudo systemctl start sshd```
2. 重啟 SSH 服務
    - 時機 : 剛設定完 SSH，要載入設定
    -  ```sudo systemctl restart sshd```
3. 關閉 SSH 服務
    - 時機 : SSH 出事情，要緊急關閉的時候
    -  ```sudo systemctl stop sshd```
4. 查看 SSH 狀態
    -  ```sudo systemctl status sshd```
5. 開機自行啟動 SSH
    - ```sudo systemctl enable sshd```

啟用防火牆
---

1. 要開啟 SSH 外部連入要把防火牆開洞
    - 如果為預設的 Port 22 : ```sudo firewall-cmd --permanent --zone=public --add-port=22/tcp```
    - 如果有修改 Port : ```sudo firewall-cmd --permanent --zone=public --add-port={修改的Port}/tcp```
        - 以 Port 66666 為例需輸入 : ```sudo firewall-cmd --permanent --zone=public --add-port=66666/tcp```
2. 重啟防火牆讓設定生效
    - 輸入 ```sudo firewall-cmd --reload```
3. 這樣就能從外部連進來了
