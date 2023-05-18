huggingface transformers
===

簡介
---

- Transformer 開發框架
- [官網](https://huggingface.co/)
- [Github](https://github.com/huggingface/transformers)

安裝方法
---

1. 建立 conda 環境
2. ```conda install -c huggingface transformers```
3. ```conda install -c tensorflow-gpu=2.5.0```

使用方法
---
1. Transformer
    - [Github](https://github.com/huggingface/transformers)
    - 可用方法
        1. 載入預訓練的模型
```
model = (
    transformers.AutoModelForSequenceClassification.from_pretrained(
        預訓練的模型名稱,
        num_labels=分類數量,
        id2label={ ID : 分類 }的 map,
        label2id={ 分類 : ID }的 map,
    ).to(torch.device("cuda" if torch.cuda.is_available() else "cpu"))
)
```
2. Tokenizers
    - [官網連結](https://github.com/huggingface/tokenizers)
    - 可用方法
        1. 使用預訓練的 Tokenize 方法
            - ```Tkz = transformers.AutoTokenizer.from_pretrained(預訓練模型名稱)```
        2. 指定使用預訓練的 Tokenize 方法
            - ```Tkz = transformers.DistilBertTokenizer.from_pretrained(預訓練模型名稱)```
        3. 使用 tokenizer 編碼 string
            - ```output_str = Tkz.(input_str, padding=True, truncation=True)```
            - input_str 可為單一字串或是字串陣列
        4. 使用 tokenizer 把編碼 string 轉回來
            - ```Revert_words = Tkz.convert_ids_to_tokens(output_str.input_ids)```
            - ```revert_str = Tkz.convert_tokens_to_string(Revert_words)```
3. Datasets
    - 連結
        - [Github](https://github.com/huggingface/datasets)
        - [官網](https://huggingface.co/datasets)
    - 要先安裝
        - ```pip install datasets```
    - 可用方法
        1. 只看資訊不下載
            - ```Info = datasets.load_dataset_builder("資料集名稱")```
        2.下載並載入資料集
            - ```DB = datasets.load_dataset("資料集名稱")```
        3. 載入自己的 Dataset
            1. 本地端
                - ```DB = datasets.load_dataset("檔案類型", data_files="資料集名稱.檔案類型")```
            2. 遠端
                - ```DB = datasets.load_dataset("檔案類型", data_files="遠端資料集網址")```
        4. 使用 stream 載入超大資料集並 Iterate 使用
            1. 指令
                - ```DB = datasets.load_dataset("json", data_files=data_files, split="train", streaming=True)```
            2. 使用資料
                - ```next(iter(DB))```
            3. shuffle
                - ```DB_shuffle = nih_dataset_streamed.shuffle(buffer_size=20_000, seed=9487)```
4. Other Library

參考來源
---
1. https://github.com/huggingface/transformers
2. https://ithelp.ithome.com.tw/articles/10291757
