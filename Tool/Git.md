![image](https://github.com/ConnectionOuOb/Share-Notebook/assets/69660530/bf19f2c7-7fc3-4aed-aaa7-6fffa0b123dd)## 大綱
### 1. 建立儲存庫
####  - 遠端
####  - 本地
### 2. 初次上傳專案
####   - 從遠端拉到本地
####   - 從本地上傳遠端
### 3. 後續工作流程
####   - 命令行模式
####   - GitHub desktop



## 建立儲存庫 (以 GitHib 為範例)
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


### 本地
1. 開啟 Terminal
2. 跳轉到以下任一種目錄，```cd {專案位置}```
    - 想要全新建立的專案
    - 想要上傳專案到 GitHib 的專案
3. 輸入指令 ```git init```
4. 建立成功



## 初次上傳專案
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
        - 版本號，如 ```v0.1.1```
        - 修改人，如 ```coneection```
        - 功能，如 ```Hot-fix_Pr87```
2. 確認是否在正確的 branch
    - 執行 ```git branch``` 後看 * 有沒有在標在你的 branch 旁邊
    - 如果沒有的話就用 ```git checkout {你的branch名稱}```
從遠端下載遠端的最新版本
 執行 ```git pull```
把檔案交給 Git ，讓 Git 開始追蹤後續修正
 執行 ```git add .```
建立一個修改版本的總結，盡量簡短到一句以內，詳細的可以後續再標註
 執行 ```git commit -m “{版本總結文字}”```
推送到遠端
 執行 ```git push```
![image](https://github.com/ConnectionOuOb/Share-Notebook/assets/69660530/a727c9af-24bc-4016-872f-66be74644407)









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

