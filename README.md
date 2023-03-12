# YOLOV5
參考來源：[YOLOV5](https://github.com/ultralytics/yolov5)
## 安裝步驟
1. 開啟Anaconda Prompt輸入```conda create -n yolov5 python=3.10```
2. 激活虛擬環境```conda activate yolov5```
3. 安裝可使用GPU的pytorch```pip install torch==1.11.0+cu113 torchvision==0.12.0+cu113 torchaudio==0.11.0+cu113 -f https://download.pytorch.org/whl/cu113/torch_stable.html```
4. 到yolov5 github官網 https://github.com/ultralytics/yolov5 Download ZIP
5. 可以從下載的檔案抓出requirement.txt或者輸入```git clone https://github.com/ultralytics/yolov5```
6. 安裝yolov5 所需要的函示庫 ```pip install -U -r yolov5/requirements.txt```
7. 透過[test_GPU.py](https://github.com/kerong2002/YOLOV5/blob/main/test_GPU.py)檢測GPU

## 訓練環境
```
(yolov5) C:\Users\User>nvidia-smi
Sun Mar 12 08:47:27 2023
+---------------------------------------------------------------------------------------+
| NVIDIA-SMI 531.14                 Driver Version: 531.14       CUDA Version: 12.1     |
|-----------------------------------------+----------------------+----------------------+
| GPU  Name                      TCC/WDDM | Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf            Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|                                         |                      |               MIG M. |
|=========================================+======================+======================|
|   0  NVIDIA GeForce GTX 1650 w...  WDDM | 00000000:01:00.0 Off |                  N/A |
| N/A   46C    P0               11W /  N/A|      0MiB /  4096MiB |      0%      Default |
|                                         |                      |                  N/A |
+-----------------------------------------+----------------------+----------------------+

+---------------------------------------------------------------------------------------+
| Processes:                                                                            |
|  GPU   GI   CI        PID   Type   Process name                            GPU Memory |
|        ID   ID                                                             Usage      |
|=======================================================================================|
|  No running processes found                                                           |
+---------------------------------------------------------------------------------------+
```

## 訓練問題&解決辦法
1. 由於NVIDIA 官方的一些軟件問題，導致了PyTorch裡面一些CUDA代碼有些問題，就是fp16（float16）數據類型在卷積等一些運算的時候會出現nan值。導致了訓練時候出現了nan值，故而在validation時就會檢測不到導致了上述情況。
2. YOLOV5裡面檢測沒有nan值、不識別問題，就只有訓練的時候有問題。
3. 在train.py搜索amp把check_amp註釋掉直接把amp賦值為False
4. 這樣做之後在運行train.py發現訓練時就不會有nan值了。如果還有，考慮下其他方法了。然後，你就會發現validation時會出現P/R/map全部為0。然後你就繼續在train.py裡面搜索half關鍵字，把所有有.half()變為.float()
5. 要解決這個問題，還需要在val.py裡面將所有的half改為False，同時im.half() if half else im.float() 改為 im.float()。



## 訓練資料
- 透過[Make Sense](https://www.makesense.ai/) 畫取標籤
- 訓練資料為my_data內容
- 訓練的標籤數量為4
```

```
names:
  0: mask
  1: parrot
  2: glasses
  3: car
```
## 訓練成品圖
![img](https://github.com/kerong2002/YOLOV5/blob/main/runs/train/exp6/val_batch0_labels.jpg)
![img](https://github.com/kerong2002/YOLOV5/blob/main/runs/train/exp6/val_batch2_labels.jpg)
