# Currency Recognition for Visually Impaired Users

This project provides a GUI-based application built using **YOLOv8** and **Tkinter**, enabling real-time currency recognition from images, videos, or live webcam input. The interface is designed to assist visually impaired users by providing visual and textual feedback about the detected currency denominations. An additional **Text-to-Speech (TTS)** feature announces the detection summary, improving accessibility.

---

## ✨ Features

* 🔍 **Object Detection** using YOLOv8 (`best.pt` fine-tuned model)
* 🖼️ Upload and analyze **images**
* 🎞️ Upload and analyze **videos**
* 📷 Use **webcam** for real-time detection
* 📋 Detection summary panel (counts and class labels)
* 💰 Shows **total amount detected** based on recognized banknotes
* 🔊 **Speak Result** button to announce detection summary
* 🔁 Automatically mirrors webcam video for a natural experience

---

## 📦 Installation & Setup

Follow these steps to deploy and run the application in **VSCode Jupyter Notebook** environment:

### 1. Clone the Repository

```bash
git clone https://github.com/NgWJ422/Currency_recognition.git
cd Currency_recognition
```

### 2. Create a Virtual Environment

Create and activate a virtual environment (recommended):

```bash
# For Windows
python -m venv venv
venv\Scripts\activate
```

### 3. Install Jupyter Kernel for VSCode

```bash
pip install ipykernel jupyter
```

### 4. Install Required Packages

Install all the required dependencies:

```bash
pip install ultralytics opencv-python pillow matplotlib torch torchvision torchaudio pyttsx3
```

---

## 📁 Project Structure

```
Currency_recognition/
|
├── colab/
│   ├── train_results/         # Training results
|   |   └──weights
|   |      └── best.pt         # Trained Yolov8 weights
│   ├── val_results/           # Validation results
│   ├── test_results/           # Testing results
│   └── currency_recognition_colab_training.ipynb    # Google Colab training notebook
├── v1.ipynb                  # Jupyter notebook GUI implementation
├── assets/                   # (Optional) Test images/videos
└── README.md
```

---

## 🧠 Notes

* Ensure your YOLOv8 model is located in `models/best.pt`.
* Webcam access may require system permission.
* This solution is designed with accessibility-focused UX by displaying predictions and class counts in real-time.
* The detection summary includes the **total amount of money** detected, based on recognized notes.
* A **Speak Result** button uses TTS to announce the current detection summary.
* The first time running the GUI cell may feel laggy or unresponsive. This is due to:

  * tkinter initializing the GUI thread within Jupyter,
  * GPU warming up and loading model weights,
  * video processing using real-time inference under limited I/O capacity.
* The webcam preview might flip and unflip briefly as the video thread stabilizes.
* Occasionally, the kernel may crash. If this happens, restart the kernel and re-run the notebook. After the initial warm-up, performance should stabilize.

---

## 🎓 Academic Context

This project was developed as part of the **BERR4743 Computer Vision and Pattern Recognition** course assignment.

**Assignment Title:** *Currency Recognition for Visually Impaired Users*

**Group Members:**

* Ng Wei Jie
* Wee Mao Phin
* Chan Zen Yang

---

## 🧠 Training Notes

The YOLOv8 model (`best.pt`) was trained on a **custom Ringgit currency dataset** using **Google Colab** to leverage GPU acceleration. After training, the best-performing model checkpoint was downloaded and placed in the `models/` directory for local inference through the Jupyter notebook. Training, validation, and testing outputs are stored in the `colab/` directory for reference.

---

## 📚 Dataset Credit

This project uses a dataset hosted on **Roboflow Universe**:

[Ringgit Currency Detection – roboflow.com](https://universe.roboflow.com/rafflesia/ringgit-currency-detection)

Special thanks to the dataset creators for their valuable contribution.

---

## 📌 To Do / Future Work

* ✅ Integrate text-to-speech for auditory feedback (completed)
* 🔄 Consider converting to standalone executable for easier deployment
