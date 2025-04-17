# 🧴 DermDetect: AI-Powered Skin Disease Classifier via Telegram 📱🧠  
### Real-Time Dermatology Assistant with Deep Learning & Chatbot Integration  
An end-to-end AI-powered solution for **real-time skin disease detection** using **Deep Learning (InceptionV3 CNN)** and a **Telegram Bot** interface. This project enables users to upload skin images via Telegram and receive instant predictions about common skin conditions such as *Tinea Ringworm*, *Candidiasis*, and *Urticaria (Hives)*.
[![Conference Paper](https://img.shields.io/badge/ICIITCEE--2025-Paper-blue)](https://ieeexplore.ieee.org/document/10915434)
[![GitHub Repo](https://img.shields.io/badge/GitHub-Explore%20Code-2ea44f)](https://github.com/Yashas14/Skin-Disease-Detector-Bot)

## 👋 Welcome to **DermDetect** 🩺📸  

Step into the future of **AI-assisted medical diagnostics** with **DermDetect** — an intelligent, lightweight solution that combines **deep learning** with a **Telegram chatbot** to identify skin diseases from images in seconds.

Whether you're in a remote location or just curious, simply send a photo via Telegram and receive a diagnosis instantly — no appointments, no apps, no hassle.

## 📌 Table of Contents

- [🧩 Project Overview](#-project-overview)
- [🚀 Features](#-features)
- [🛠️ Technologies Used](#️-technologies-used)
- [🧠 Why InceptionV3?](#-why-inceptionv3)
- [📁 Dataset](#-dataset)
- [⚙️ How It Works](#️-how-it-works)
- [📲 Telegram Bot Interface](#-telegram-bot-interface)
- [🧪 Model Training](#-model-training)
- [🖥️ Local Setup](#️-local-setup)
- [🎯 Future Improvements](#-future-improvements)


## 🧩 Project Overview

This project bridges **AI and accessibility** by building a platform where users can simply send an image through Telegram and instantly receive a prediction about possible skin diseases. It is especially useful in remote or resource-constrained settings where access to dermatological consultations is limited.

The model is built using **InceptionV3**, a powerful deep learning architecture fine-tuned for medical image classification. It is integrated into a lightweight **Telegram bot** that handles image input, pre-processing, prediction, and response—all in real time.

## 💡 Motivation

Access to dermatologists is often limited — especially in rural or resource-constrained environments. We wanted to:

- Democratize access to **early skin diagnostics**  
- Build a tool that’s easy to use for **any age group**  
- Showcase the power of **deep learning + chatbot interaction**  
- Keep it **lightweight**, **secure**, and **real-time**  

## 🚀 Features

- 🏥 Detects skin conditions like *Tinea Ringworm*, *Candidiasis*, and *Urticaria*
- 🤖 Deep Learning model using InceptionV3 (Transfer Learning)
- 📱 User-friendly Telegram Bot Interface
- 🔎 Real-time image processing and disease classification
- 📦 Efficient deployment using lightweight model format (`.keras`)
- 🧼 Auto image cleanup post-prediction
- 🔒 Private and offline predictions (can be hosted locally)



## 🛠️ Technologies Used

| Tool/Library      | Purpose                                  |
|------------------|------------------------------------------|
| Python            | Core programming language                |
| TensorFlow / Keras| Model building and training              |
| NumPy             | Numerical operations                     |
| OpenCV / PIL      | Image processing                         |
| Telegram Bot API  | Real-time chat interface with bot        |
| `python-telegram-bot` | Handling bot commands and messages   |
| Google Colab      | Model training environment               |



## 🧠 Why InceptionV3?

InceptionV3 is a high-performing Convolutional Neural Network architecture developed by Google. It is particularly well-suited for medical image classification because:

- 🔍 **Deep architecture with fewer parameters**: Optimized computational cost while maintaining accuracy.
- 🧬 **Handles complex patterns** in high-resolution images.
- 🎯 **Pre-trained on ImageNet**: Transfer learning allows leveraging vast knowledge for small medical datasets.
- 🏃 **Efficient at inference time**, enabling near real-time predictions.
-  📈 **Superior performance on medical image datasets**

We use **Transfer Learning**, fine-tuning the pre-trained InceptionV3 on a custom dataset of skin disease images.



## 📁 Dataset

- Custom-curated dataset containing images of:
  - **Tinea/Ringworm/Candidiasis and other Fungal Infections**
  - **Urticaria (Hives)**
- Images were resized to `300x300` pixels for model compatibility.
- Split into training and testing sets for validation.
- Data Augmentation was applied to improve generalization.

> **Note**: Due to medical data restrictions, the dataset is not included in this repository. Please contact for access or use open dermatology image sources like HAM10000 or DermNet.



## ⚙️ How It Works

### 🔄 Flow:
1. **User** sends an image of a skin condition to the **Telegram bot**.
2. Bot saves the image temporarily.
3. Preprocesses it into a format compatible with the trained model (`300x300` pixels, normalized).
4. Loads the trained model from a `.keras` file.
5. Runs the image through the **InceptionV3 CNN**.
6. Predicts the class (e.g., Tinea, Urticaria).
7. Sends back the disease name as a reply.



## 📲 Telegram Bot Interface

The bot is built using the [`python-telegram-bot`](https://github.com/python-telegram-bot/python-telegram-bot) library.

### 🔧 Setup:
- You must create a bot using [@BotFather](https://core.telegram.org/bots#6-botfather).
- Replace the bot token in `telegram_bot_interface_new.py` with your own.

```python
application = Application.builder().token('YOUR_TELEGRAM_BOT_TOKEN').build()
```


## 🧪 Model Training

Training the AI to become your skin specialist wasn't easy — but here's how we taught it to *see*.

| Step                     | Description                                                                 |
|--------------------------|-----------------------------------------------------------------------------|
| 🖼️ **Image Preprocessing** | Resized all images to `300x300`, normalized pixel values between 0-1         |
| 🧠 **Model Architecture**   | Transfer Learning using **InceptionV3** (pretrained on ImageNet)            |
| 🧪 **Fine-Tuning**          | Last few layers unfrozen and retrained for domain-specific features         |
| 🔧 **Loss Function**        | Categorical Crossentropy for multi-class classification                    |
| 🚀 **Optimizer**            | Adam with a learning rate of 0.0001                                         |
| 📊 **Metrics**              | Accuracy and Validation Accuracy tracked during training                   |

The model was trained on **Google Colab** for flexibility and speed, and saved in `.keras` format for lightweight deployment.



## 🖥️ Local Setup

Want to try it yourself? Here's how to launch your very own **AI skin bot** locally 🚀

### 🔧 Prerequisites
- Python 3.8 or higher
- Telegram Bot Token (create one via [@BotFather](https://t.me/BotFather))
- A trained `.keras` model (included or replaceable)

### 🪄 Installation Steps

```bash
# 1. Clone the repo
git clone https://github.com/Yashas14/Skin-Disease-Detector-Bot.git
cd Skin-Disease-Detector-Bot

# 2. Create and activate a virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# 3. Install dependencies
pip install -r requirements.txt

# 4. Replace your Telegram bot token in `telegram_bot_interface_new.py`
application = Application.builder().token('YOUR_BOT_TOKEN').build()

# 5. Run the bot
python telegram_bot_interface_new.py
```

### 📦 Requirements

```txt
tensorflow
numpy
Pillow
python-telegram-bot==20.0a6
```

Once it's running, open your Telegram app, search for your bot, and send a skin image to see it in action! ⚡



## 🎯 Future Improvements

This is just the beginning. Here's what’s coming next for **DermDetect**:

| Improvement                        | Goal                                                                 |
|------------------------------------|----------------------------------------------------------------------|
| 🧬 **Expand Disease Categories**     | Add more conditions like Eczema, Psoriasis, Acne, etc.               |
| ☁️ **Cloud Deployment**             | Host the model via Flask/FastAPI on AWS, GCP, or Railway             |
| 🔍 **Explainable AI**               | Integrate Grad-CAM or LIME for visual heatmap-based predictions      |
| 🌍 **Multilingual Bot Support**     | Enable diagnosis in regional languages like Hindi, Kannada, Tamil   |
| 📉 **Model Optimization**           | Reduce size with quantization or ONNX conversion for mobile use      |
| 👨‍⚕️ **Doctor Feedback Loop**        | Add expert feedback to improve model accuracy over time              |
| 📲 **Mobile App Integration**       | Extend beyond Telegram — bring the model to Android/iOS apps         |

> ⚡ *We’re committed to improving accessibility, accuracy, and trust in AI-powered health tech.*


## 📫 Contact

For questions, suggestions, or collaboration ideas, reach out to:  
**Yashas D**  
📧 [GitHub Profile](https://github.com/Yashas14)  
🌐 [Project Repository](https://github.com/Yashas14/Seamless_Interaction_through_Gesture_Recognition)
🔗 **LinkedIn**: [Yashas D on LinkedIn](https://www.linkedin.com/in/yashasd2004/) 

