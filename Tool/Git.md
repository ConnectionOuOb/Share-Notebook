# Git / GitHub 筆記
## 大綱
1. [簡介](#簡介)
2. [建立儲存庫](#建立儲存庫-以-github-為範例)
    - [本地](#本地)
    - [遠端](#遠端)
3. [專案建置設定](#專案建置設定)
    - [從遠端拉到本地](#從遠端拉到本地)
    - [從本地上傳遠端](#從本地上傳遠端)
4. [後續工作流程](#後續工作流程)
    - [命令行模式](#命令行模式)
    - [GitHub desktop](#github-desktop)
5. [附錄](#附錄)
6. [參考](#參考)



## 簡介
- Git 的功能
    - 版本控制
        - 為專案每個時間的修改賦予一組總結的代碼，便於後續追蹤
    - 團隊協作
        - 透過分支的創建與合併，讓不同人得以在同一專案上有序地協作
- Git 的架構
    - ![image](https://github.com/ConnectionOuOb/Share-Notebook/assets/69660530/e5e3e997-774c-482e-9a66-f148edf1d879)




## 建立儲存庫 (以 GitHub 為範例)
### 本地
1. 開啟 Terminal
2. 跳轉到以下任一種目錄，```cd {專案位置}```
    - 想要全新建立的專案
    - 想要上傳專案到 GitHib 的專案
3. 輸入指令 ```git init```
4. 建立成功


###  遠端
1. 登入 [GitHub](https://github.com/login)
2. 登入成功後導航到 [Dashboard](https://github.com/)
3. 點選圖片中 **New** 按鈕
![image](https://github.com/ConnectionOuOb/Share-Notebook/assets/69660530/a6d409b7-eaa8-4fb2-90b2-50659cb0cf9a)
4. 新 Repository 設定
![image](https://github.com/ConnectionOuOb/Share-Notebook/assets/69660530/ea2b275b-c898-48bb-933f-98fc2c8055b7)
    - Owner
        - 可以選擇讓新儲存庫建立到個人或是組織
    - Repository name
        - 設定新儲存庫的名稱，不能與 Owner 設定儲存的地方裡面的專案相同名稱
    - Description (optional)
        - 專案簡短說明，可留空
    - Public / Private
        - Public 是指網路上任何人都可以看到這個儲存庫
        - Private 模式
            - Owner 建立到個人
                - 預設只有自己看的到
                - 可以另外給其他人權限
            - Owner 建立到組織
                - 預設只有自己以及組織的最高權限擁有者看的到
                - 可以另外給其他人或是其他 Team 權限
5. 初始化設定
6. 點選 **Create Repository** 按鈕
7. 建立成功



## 專案建置設定
1. 開啟 Terminal
2. 跳轉到放專案的目錄，```cd {目錄位置}```

### 從遠端拉到本地
1. 使用 clone 指令複製到本地
    - 經由 https
        - 格式 : ```git clone https://github.com/{Owner名稱}/{儲存庫名稱}.git```
        - 例如 : ```git clone https://github.com/ConnectionOuOb/Test123.git```
    - 經由 ssh
        - 格式 : ```git clone git@github.com:{Owner名稱}/{儲存庫名稱}.git```
        - 例如 : ```git clone git@github.com:ConnectionOuOb/Test123.git```

### 從本地上傳遠端
#### 初次上傳
1. 確認已經做過 ```git init``` (確認 **".git/"** 資料夾是否存在)
2. 執行 ```git commit -m "First commit"``` 來說明這次上傳行為
3. 因為 GitHub 遠端預設 branch 是 **main** 而非 **master**，所以要執行 ```git branch -M main"``` 把 **master branch** 修改成 **main branch**
4. 設定遠方代碼庫位置
    - 因為權限因素，建議採用 ssh 儲存庫位置
    - 經由 https
        - 格式 : ```git remote add origin https://github.com/{Owner名稱}/{儲存庫名稱}.git```
        - 例如 : ```git remote add origin https://github.com/ConnectionOuOb/Test123.git```
    - 經由 ssh
        - 須先新增機器的 ssh public 金鑰到 Github 後再執行後續步驟，設定方法參考最後方附錄
        - 格式 : ```git remote add origin git@github.com:{Owner名稱}/{儲存庫名稱}.git```
        - 例如 : ```git remote add origin git@github.com:ConnectionOuOb/Test123.git```
5. 推送並更新遠端 branch ```git push -u origin main```

#### 非初次上傳
1. 設定遠方代碼庫位置
    - 因為權限因素，建議採用 ssh 儲存庫位置
    - 經由 https
        - 格式 : ```git remote add origin https://github.com/{Owner名稱}/{儲存庫名稱}.git```
        - 例如 : ```git remote add origin https://github.com/ConnectionOuOb/Test123.git```
    - 經由 ssh
        - 須先新增機器的 ssh public 金鑰到 Github 後再執行後續步驟，設定方法參考最後方附錄
        - 格式 : ```git remote add origin git@github.com:{Owner名稱}/{儲存庫名稱}.git```
        - 例如 : ```git remote add origin git@github.com:ConnectionOuOb/Test123.git```
2. 確保有 main branch ```git branch -M main```
3. 推送並更新遠端 branch ```git push -u origin main```



## 後續工作流程
![GitWorkflow](https://github.com/ConnectionOuOb/Share-Notebook/assets/69660530/19d5d9a4-f397-4744-918b-ced9a47f486d)
### 命令行模式
1. 建立新 branch
    - branch 名稱建議有規律並且統一，可為:
        - (最建議) 版本號，如 **v0.1.1**
        - (建議) 修改人，如 **coneection**
        - 新功能，如 **Search-Algp** 或 **Hot-fix_PR-10**
    - 使用 ```git branch {branch 名稱}``` 建立
    - 以 connection 為例，就是 ```git branch connection```
2. 確認是否在正確的 branch
    - 直接執行 ```git branch``` 後看 * 符號有沒有在標在你的 branch 旁邊
        - 如果沒有的話就用 ```git checkout {你的branch名稱}``` 來切到你的 branch
        - 以 connection 為例，就是 ```git checkout connection```
3. 進行檔案修改，可以用 ```git status``` 看當前已經修改了哪些部分
4. 從遠端下載遠端的最新版本
    - 執行 ```git pull```
5. 把檔案交給 Git ，讓 Git 開始追蹤後續修正
    - 執行 ```git add .``` 讓全部檔案被追蹤
    - 或是只想追蹤特定檔案 ```git add {特定檔案}```
6. 建立一個對修改內容的總結，簡短到一句以內，詳細的描述後續可以再標註
    - 執行 ```git commit -m “{修改內容總結文字}”```
    - 例如 ```git commit -m “v240423_1239”```
7. 執行 ```git push``` 推送到遠端


### GitHub Desktop
- 僅限 PC 能使用
- Unix/Linux Server 只能用上一部份的命令列
- 要另外裝 [GitHub desktop](https://desktop.github.com/)
- 登錄自己的 GitHub 帳號



## 合併分支
- 功能都開發完成後，可以進行 branch 的整併

### 如果遠端儲存庫在 GitHub
1. 開啟專案的 GitHub 網頁
2. 點選 **Pull Request** 按鈕



## 附錄
### 設定機器的 ssh public 金鑰到 Github
1. 開啟要上傳的機器的 Terminal
2. 輸入 ```ssh-keygen -t ed25519 -C "{你的Email}"```，一定不能用預設的加密算法
3. 生成金鑰後，開啟提示中出現的檔案位置 (圖片中黃色部分)
![image](https://github.com/ConnectionOuOb/Share-Notebook/assets/69660530/2f2da0f0-233a-41b3-86e7-102d2937c23a)
4. 複製金鑰，理論上格式要是 ```ssh-ed25519 .....{金鑰本文}..... {你的Email}```
5. 開啟 GitHub [Dashboard](https://github.com/)
6. 點選右上方頭像
![image](https://github.com/ConnectionOuOb/Share-Notebook/assets/69660530/15ca5ff0-927f-488d-8fab-67b66f047caf)
7. 點選 **Setting**
![image](https://github.com/ConnectionOuOb/Share-Notebook/assets/69660530/dd78b56f-b6cf-4261-85d1-ee3b689d363b)
8. 點選左側的 **SSH and GPG keys**，然後點選右方的 **New SSH key** 按鈕
![image](https://github.com/ConnectionOuOb/Share-Notebook/assets/69660530/a27bf0b1-7afb-420f-9b60-e2c2b45b6cd0)
9. 貼上金鑰後儲存即可完成設定
![image](https://github.com/ConnectionOuOb/Share-Notebook/assets/69660530/801c9be0-8cb7-401c-8cfb-99c0a4a7dec1)


### 其餘指令
#### 設定姓名和 Email
1. ```git config --global user.name "{你的名字}"```
2. ```git config --global user.email {你的Email}```

#### 列出使用者資料
- ```git config --list```

#### 檢視 commit 紀錄
- ```git log```


## 參考
- https://medium.com/@flyotlin/%E6%96%B0%E6%89%8B%E4%B9%9F%E8%83%BD%E6%87%82%E7%9A%84git%E6%95%99%E5%AD%B8-c5dc0639dd9


