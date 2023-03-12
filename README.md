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
## 訓練資料
- 透過[Make Sense](https://www.makesense.ai/) 畫取標籤
- 訓練資料為my_data內容
- 訓練的標籤數量為4
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
