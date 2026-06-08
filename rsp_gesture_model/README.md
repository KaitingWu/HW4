# Rock-Paper-Scissors Gesture Recognition Model (剪刀石頭布手勢辨識模型)

這是一個基於機器學習與深度學習的「剪刀、石頭、布」手勢辨識專案。本專案實作了多種模型（包含 SVM、自訂 CNN 以及 MobileNet 遷移學習模型），並提供了完整的訓練腳本與測試程式。

## 📁 專案架構 (Project Structure)

```text
rsp_gesture_model/
├── dataset/                  # 資料集目錄 (包含 train 與 test 資料夾，內含 rock/paper/scissors 圖片)
├── train/                    # 模型訓練相關程式碼
│   ├── train_cnn.py          # 訓練自訂 CNN 模型 (TensorFlow/Keras)
│   ├── train_mobilenet.py    # 訓練 MobileNet 遷移學習模型 (TensorFlow/Keras)
│   ├── train_svm.py          # 訓練 SVM 傳統機器學習模型 (scikit-learn)
│   ├── camera_demo.py        # 使用攝影機即時預測手勢的 Demo 程式
│   └── requirements.txt      # 訓練環境所需的套件清單
├── demo/                     # 測試與 Demo 相關程式碼
│   ├── test.py               # 使用測試集評估 SVM 模型準確率的測試腳本
│   ├── carema.py             # 簡單的 OpenCV 攝影機擷取畫面測試腳本
│   ├── rps_svm_model.pkl     # 訓練好的 SVM 模型權重檔
│   └── requirements.txt      # 測試與 Demo 環境所需的套件清單
├── hw4/                      # 相關作業或參考檔案
├── Claude_chat.pdf / Gemini_chat.pdf # AI 開發討論對話紀錄
├── cnn_result.jpg            # CNN 模型評估結果圖
├── mobilenet_result.jpg      # MobileNet 模型評估結果圖
├── demo_vid.mp4              # 實際 Demo 影片
└── README.md                 # 專案說明文件
```

## 🛠️ 環境建置 (Environment Setup)

請先確保您的環境已經安裝了 Python。您可以透過以下指令安裝所需的套件：

### 訓練環境安裝 (針對 `train/` 資料夾)
若您想重新訓練模型，請進入 `train` 資料夾安裝所需套件：
```bash
cd train
pip install -r requirements.txt
```
套件包含：`opencv-python`, `scikit-learn`, `numpy`, `joblib`, `tensorflow>=2.13.0`

### 測試環境安裝 (針對 `demo/` 資料夾)
若您只想測試現有的 SVM 模型，請進入 `demo` 資料夾安裝：
```bash
cd demo
pip install -r requirements.txt
```
套件包含：`scikit-learn`, `opencv-python`, `numpy`, `joblib`, `mediapipe`

## 🚀 如何執行 (How to Run)

### 1. 模型訓練 (Training Models)
進入 `train/` 目錄，選擇您想要訓練的模型腳本：
- **訓練 SVM 模型**（訓練完成後會自動將 `.pkl` 存入 `demo/`）：
  ```bash
  python train_svm.py
  ```
- **訓練 CNN 模型**：
  ```bash
  python train_cnn.py
  ```
- **訓練 MobileNet 模型**：
  ```bash
  python train_mobilenet.py
  ```

### 2. 模型測試與評估 (Testing & Evaluation)
進入 `demo/` 目錄，您可以測試已訓練好的 SVM 模型在測試集（`dataset/test`）上的表現：
```bash
python test.py
```

### 3. 即時攝影機 Demo (Real-time Camera Demo)
在 `train/` 目錄下，您可以執行即時攝影機手勢辨識：
```bash
python camera_demo.py
```
*(注意：若要單純測試攝影機是否正常運作，可執行 `demo/carema.py`)*

## 📊 模型與效能 (Models & Performance)
本專案嘗試了不同的電腦視覺方法，從傳統的機器學習 SVM（配合灰階與縮放預處理），到深度學習的自訂 Convolutional Neural Network (CNN)，再到使用 Pre-trained MobileNet 進行遷移學習，藉此比較不同模型在手勢辨識任務上的準確率與效能。評估結果可參考根目錄下的 `cnn_result.jpg` 與 `mobilenet_result.jpg`。