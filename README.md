# YOLOV5
YOLOV5
## 安裝步驟
1. 開啟Anaconda Prompt輸入```conda create -n yolov5 python=3.10```
2. 激活虛擬環境```conda activate yolov5```
3. 安裝可使用GPU的pytorch```pip install torch==1.11.0+cu113 torchvision==0.12.0+cu113 torchaudio==0.11.0+cu113 -f https://download.pytorch.org/whl/cu113/torch_stable.html```
4. 到yolov5 github https://github.com/ultralytics/yolov5 Download ZIP
5. 可以從下載的檔案抓出requirement.txt或者輸入```git clone https://github.com/ultralytics/yolov5```
6. 安裝yolov5 所需要的函示庫 ```pip install -U -r yolov5/requirements.txt```

## 訓練
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
