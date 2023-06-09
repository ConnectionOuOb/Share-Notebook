MariaDB 設定方式
===

安裝
---

1. 開啟要設定的電腦的 Terminal
2. 用有管理權限的帳號執行 ```sudo yum install mariadb-server```
3. 安裝完成

服務控制
---

1. 開啟 MariaDB 服務
    - 時機 : FTP 是關閉的時候
    - ```sudo systemctl start mariadb```
2. 重啟 MariaDB 服務
    - 時機 : 剛設定完 MariaDB，要載入設定
    -  ```sudo systemctl restart mariadb```
3. 關閉 MariaDB 服務
    - 時機 : FTP 出事情，要緊急關閉的時候
    -  ```sudo systemctl stop mariadb```
4. 查看 MariaDB 狀態
    -  ```sudo systemctl status mariadb```
5. 開機自行啟動 MariaDB
    - ```sudo systemctl enable mariadb```

安全性設定
---

- 執行 ```sudo mysql_secure_installation```，按照他的提示設定

修改資料庫儲存位置
---
1. ```sudo systemctl stop mariadb.service``` 停止服務
2. 目標儲存位置目錄設定
    1. ```mkdir {要存的目錄}```
    2. ```chmod 700 {要存的目錄}```
    3. ```sudo chown mysql.mysql {要存的目錄}```
3. ```sudo cp -rp /var/lib/mysql/* {要存的目錄}``` 複製舊的位置到新資料夾
4. 修改設定 ```sudo vim /etc/my.cnf``` ，在 ```[mysqld]``` 段落
    - ```datadir={要存的目錄}```
    - ```socket={要存的目錄}/mysql.sock```
5. ```sudo systemctl start mariadb``` 啟動 MariaDB 伺服器
6. 修改完成

常用指令
---

- 登入資料庫的 CLI 介面
    - ```mysql -u {使用者} -p```
    - 例如用 root 登入 ```mysql -u root -p```
- 登出
    - ```exit```

參考來源
---
1. https://blog.gtwang.org/linux/centos-7-install-mariadb-mysql-server-tutorial/
