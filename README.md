<p align="center">
  <img src="./capturas/logo.png" alt="logo" width="160"/>
</p>

<h1 align="center">🧠 Stroke Predictor — Clinical ML + CNN on Brain MRI</h1>

<p align="center">
  Estimates stroke risk in two ways: from a patient's clinical data (tabular ML)<br/>
  and from brain MRI images (Convolutional Neural Network in PyTorch).
</p>

<p align="center">
  <img src="https://img.shields.io/badge/PyTorch-EE4C2C?logo=pytorch&logoColor=white" />
  <img src="https://img.shields.io/badge/TensorFlow-FF6F00?logo=tensorflow&logoColor=white" />
  <img src="https://img.shields.io/badge/scikit--learn-F7931E?logo=scikit-learn&logoColor=white" />
  <img src="https://img.shields.io/badge/FastAPI-009688?logo=fastapi&logoColor=white" />
  <img src="https://img.shields.io/badge/React-20232A?logo=react&logoColor=61DAFB" />
  <img src="https://img.shields.io/badge/Tailwind-38B2AC?logo=tailwind-css&logoColor=white" />
  <img src="https://img.shields.io/badge/Docker-2496ED?logo=docker&logoColor=white" />
  <img src="https://img.shields.io/badge/Supabase-3ECF8E?logo=supabase&logoColor=white" />
</p>

> ⚠️ Educational project. Not a medical device and not intended for clinical use.

---

## 🎯 The problem

Stroke is one of the leading causes of death and disability, and early risk detection matters. This project explores two complementary signals: routine clinical data (age, hypertension, glucose, BMI…) and brain MRI scans.

## 📊 Results

| Model | Input | Result |
|---|---|---|
| **CNN (PyTorch)** | Brain MRI images ([NSC-MRI dataset](https://universe.roboflow.com/wtnny/nsc-mri/dataset/7)) | **93% accuracy · ROC-AUC 0.98 · overfitting < 2%** |
| Random Forest + RandomUnderSampler | Clinical form data | 77% accuracy on a highly imbalanced dataset |

<p align="center">
  <img src="./capturas/metricas-cnn.png" alt="CNN metrics" width="420"/>
</p>

**How the CNN got there:** a first CNN in TensorFlow/Keras plateaued around 62% accuracy (AUC 0.64). Rebuilding the network in PyTorch and tuning the optimizer raised it to 93% accuracy with an AUC of 0.98 while keeping the train/validation gap under 2%.

## ✨ Features

- **Two prediction modes** in the web app: clinical form or MRI image upload
- **Model selection** across several classifiers, with class imbalance handling
- **FastAPI** backend serving both models, **React + Vite + Tailwind** frontend
- **Prediction history** stored in Supabase
- **Docker Compose** setup and **pytest** suite (API, helpers, model loader, image prediction)

<p align="center">
  <img src="./capturas/frontend-render.png" alt="Web app" width="700"/>
</p>

## 🏗️ Architecture

<p align="center">
  <img src="./capturas/Diagrama_stroke_predict.drawio.png" alt="Architecture" width="650"/>
</p>

## 👤 My role

Team project of 4 at the Factoría F5 AI Bootcamp. I worked as **data engineer and deep learning engineer**:

- Exploratory data analysis and dataset updates
- Model class and comparison of classical models against a dense neural network
- **CNN for MRI classification**: first version in TensorFlow/Keras, then the PyTorch CNN used in production, including optimizer tests and tuning

## 🚀 Run it locally

```bash
git clone https://github.com/mr-melenas/stroke-predictor-cnn.git
cd stroke-predictor-cnn
cp .env.example .env          # Supabase credentials
# Download model.pkl and cnn_pytorch.pth from the original repo's Releases into data/
docker compose up --build
```

## 👥 Team

Built at [Factoría F5](https://factoriaf5.org/) by [@mr-melenas](https://github.com/mr-melenas) (Max Beltrán), [@alharuty](https://github.com/alharuty) (Alla Haruty), [@Omarlsant](https://github.com/Omarlsant) (Omar Lengua) and [@merkandez](https://github.com/merkandez) (César Mercado).
Original team repository: [Bootcamp-IA-P4/Proyecto-IX-DS2](https://github.com/Bootcamp-IA-P4/Proyecto-IX-DS2) · Model files: [Releases](https://github.com/alharuty/Proyecto-IX-DS2/releases).
