Ultimate Vocal Remover GUI v5.5.0
===

簡介
---

- 去除人聲軟體
- 官方網站 : [傳送門](https://github.com/Anjok07/ultimatevocalremovergui)

安裝方法
---

1. 根據系統下載對應版本並安裝
    - [載點](https://github.com/Anjok07/ultimatevocalremovergui/releases/tag/v5.5.0)

可用指令
---
1. Windows 批量改檔案名
    1. 開啟目錄位置的 Terminal
    2. 輸入 ```Dir *.{**來源格式**} | %{Rename-Item $_ -NewName ("{**新名稱**}-{0}.{**來源格式**}" -f $c++)}```
    3. 例如 ```Dir *.mp3 | %{Rename-Item $_ -NewName ("newName-{0}.mp3" -f $c++)}```

參考來源
---
1. https://github.com/Anjok07/ultimatevocalremovergui
