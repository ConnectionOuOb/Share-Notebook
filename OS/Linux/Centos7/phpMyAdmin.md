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

修改連入設定
---

1. 編輯設定檔 ```sudo vim /etc/httpd/conf.d/phpMyAdmin.conf```
2. 修改預設的 IP 127.0.0.1 成可登入的 IP
    - 有一行是 ```Require ip 127.0.0.1```
    - 該行修改成 ```Require ip {可登入 IP}```
    - 或是使用語法
        1. ```Require all denied``` 全部不要
        2. ```Require all granted``` 全部都要
        3. ```Require host {網域名稱}``` 特定網域名稱內可連線
        4. ```Require ip {網段}``` 特定網段內可連線
            - 例如網段 192.168.0.0 就是 ```Require ip 192.168```
        5. ```Require ip {IP/CIDR}``` 特定網段內可連線 IP/CIDR
            - 例如網段 192.168.0.0 就是 ```Require ip 192.168.0.0/16```
3. 按 **esc**，然後輸入 ```:wq``` 儲存後離開
4.  httpd ```sudo systemctl restart httpd```
5. 設定完成
