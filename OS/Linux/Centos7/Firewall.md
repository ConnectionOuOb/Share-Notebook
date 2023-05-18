防火牆設定
===

安裝
---
1. 開啟要設定的電腦的 Terminal
2. 檢查另一個防火牆軟體是否正在運行，兩者只能擇一
    - 輸入 ```sudo systemctl status iptables```，沒出現正在使用中就可以進 3. 了
    - 如果 iptables 正在執行，輸入 ```sudo systemctl stop iptables``` 關閉它
    - 最後輸入 ```sudo systemctl mask iptables``` 把 iptables 永久禁用
3. 用有管理權限的帳號執行 ```sudo yum -y install firewalld```
4. 安裝完成

常用設定
---
1. 查看所有設定
    - ```sudo firewall-cmd --list-all```
2. 重新載入設定
    - ```sudo firewall-cmd --reload```
3. 開啟特定 port 通過防火牆
    - ```sudo firewall-cmd --permanent --zone=public --add-port={要通過的Port}/tcp```
    - 假設要開啟 port 1234，就輸入 ```sudo firewall-cmd --permanent --zone=public --add-port=1234/tcp```
4. 開啟特定服務通過防火牆
    - ```sudo firewall-cmd --permanent --zone=public --add-service={要通過的服務}/tcp```
    - 假設要開啟 FTP，就輸入 ```sudo firewall-cmd --permanent --zone=public --add-service=ftp```

服務控制
---

1. 開啟 firewalld 服務
    - 時機 : FTP 是關閉的時候
    - ```sudo systemctl start firewalld```
2. 重啟 firewalld 服務
    - 時機 : 剛設定完 firewalld，要載入設定
    -  ```sudo systemctl restart firewalld```
3. 關閉 firewalld 服務
    - 時機 : firewalld 出事情，要緊急關閉的時候
    -  ```sudo systemctl stop firewalld```
4. 查看 firewalld 狀態
    -  ```sudo systemctl status firewalld```
5. 開機自行啟動 firewalld
    - ```sudo systemctl enable firewalld```

參考來源
---
1. https://blog.gtwang.org/linux/centos-7-firewalld-command-setup-tutorial/
