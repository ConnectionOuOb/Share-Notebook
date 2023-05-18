Proxmox 通訊阜轉接
===

用途
---
1. 把虛擬機的特定端口導向到 host 的特定端口
    - 例如把 VM-1 的 SSH port (22) 導向到 host 的 port 22222
    - 例如把 VM-2 的 RDP port (3389) 導向到 host 的 port 22389
2. 目前第 7 版的 Proxmox 的管理網頁沒有這功能的 UI，需要用指令列操作

設定方式
---
1. 開啟 host 命令列
2. 輸入 ```nano /etc/network/interfaces``` 修改網路設定檔案
3. 修改內容如下
```
auto lo
iface lo inet loopback
iface {外網IP的網卡名稱} inet manual

auto vmbr1
iface vmbr1 inet static
        address {外網IP/CIDR}
        gateway {外網Gateway}
        bridge-ports {外網IP的網卡名稱}
        bridge-stp off
        bridge-fd 0

auto vmbr2
iface vmbr2 inet static
        address {虛擬網段IP/CIDR}
        bridge-ports none
        bridge-stp off
        bridge-fd 0

post-up echo 1 > /proc/sys/net/ipv4/ip_forward
post-up iptables -t nat -A POSTROUTING -s '{虛擬網段IP/CIDR}' -o vmbr1 -j MASQUERADE
post-down iptables -t nat -D POSTROUTING -s '{虛擬網段IP/CIDR}' -o vmbr1 -j MASQUERADE
post-up   iptables -t raw -I PREROUTING -i fwbr+ -j CT --zone 1
post-down iptables -t raw -D PREROUTING -i fwbr+ -j CT --zone 1
```
4. 按 **Ctrl+X**，輸入 ```y``，儲存這個設定檔案
5. 再命令列輸入 ```iptables -t nat -A PREROUTING -p tcp -d {外網IP} --dport {對外port} -i vmbr1 -j DNAT --to-destination {虛擬機IP}:{虛擬機port}``` 設定導向規則
    - 例如要從外網 IP **123.123.123.123** 的機器的 port 33899 轉接進內網 IP 為 10.10.10.10的虛擬機 port 3389，設定就會像這樣
    - ```iptables -t nat -A PREROUTING -p tcp -d 123.123.123.123 --dport 33899 -i vmbr1 -j DNAT --to-destination 10.10.10.10:3389```
6. 輸入 ```systemctl restart networking``` 重啟網路服務
7. 完成
