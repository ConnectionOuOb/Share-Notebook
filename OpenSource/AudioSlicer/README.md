Ultimate Vocal Remover GUI v5.5.0
===

簡介
---

- 音檔切分 Python 腳本
- 官方網站 : [傳送門](https://github.com/openvpi/audio-slicer)

下載方法
---

下載這個腳本 : [載點](https://raw.githubusercontent.com/openvpi/audio-slicer/main/slicer2.py)

指令
---
- 指令
	- ```python slicer2.py audio [--out OUT] [--db_thresh DB_THRESH] [--min_length MIN_LENGTH] [--min_interval MIN_INTERVAL] [--hop_size HOP_SIZE] [--max_sil_kept MAX_SIL_KEPT]```
- 參數
	- sr : 音源採樣率
	- db_threshold : RMS 的大小，比這小都靜音，用來排除很多噪音，預設 -40
	- min_length : 最小長度，單位是毫秒 (milliseconds)，預設 5000
	- min_interval : 靜音部分最小間隔，單位是毫秒 (milliseconds)，預設 300
	- hop_size : RMS frame rate，預設 10
	- max_silence_kept : 切片音頻周圍的最大靜音長度，預設 1000

參考來源
---
1. https://github.com/openvpi/audio-slicer
