# 🧠 Mansik Santulan — Mental Health Score Predictor

![Python](https://img.shields.io/badge/Python-3.9%2B-blue?style=for-the-badge&logo=python&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-0.100%2B-009688?style=for-the-badge&logo=fastapi&logoColor=white)
![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white)
![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)

An end-to-end Machine Learning web application that predicts an individual's **Mental Health Score** based on daily lifestyle, academic habits, physical wellness, and social media usage patterns. Built from data exploration and model training to a decoupled REST API backend and responsive frontend interface.

---

## 📋 Table of Contents
- [Overview](#-overview)
- [Key Features](#-key-features)
- [Dataset Description](#-dataset-description)
- [Tech Stack](#-tech-stack)
- [Project Architecture & Structure](#-project-architecture--structure)
- [Machine Learning Pipeline](#-machine-learning-pipeline)
- [Installation & Local Setup](#-installation--local-setup)
- [API Usage](#-api-usage)
- [Future Improvements](#-future-improvements)
- [Disclaimer](#-disclaimer)
- [Acknowledgments](#-acknowledgments)

---

## 🔍 Overview

In an increasingly connected digital world, screen time, social media habits, sleep quality, and academic pressure heavily influence student well-being. **Mansik Santulan (Mental Health Score Predictor)** leverages supervised regression modeling to quantify how behavioral and lifestyle metrics impact mental wellness on a continuous scale.

This project covers the complete Machine Learning lifecycle:
1. **Exploratory Data Analysis (EDA) & Preprocessing** in Jupyter Notebook.
2. **Feature Engineering & Model Selection** to optimize predictive accuracy.
3. **Model Serialization** using `joblib`/`pickle` for low-latency inference.
4. **Backend API Development** using **FastAPI** to serve predictions over HTTP.
5. **Interactive Web Interface** built with vanilla **HTML, CSS, and JavaScript** for real-time user interaction.

---

## ✨ Key Features

- **Real-Time Predictions:** Instantaneous mental health score calculation upon submitting lifestyle parameters.
- **End-to-End ML Pipeline:** Includes data cleaning, outlier handling, categorical encoding, and feature scaling baked directly into the inference workflow.
- **Decoupled Architecture:** Clean separation between the FastAPI backend inference engine and the lightweight frontend client.
- **Interactive UI:** User-friendly form interface with input validation and clear score visualization.
- **Production-Ready API:** Includes interactive Swagger UI documentation (`/docs`) out of the box via FastAPI.

---

## 📊 Dataset Description

The model is trained on the **Student Social Media and Mental Health Impact** dataset (`5,000` records across `13` attributes), capturing demographic, behavioral, and wellness indicators:

| Feature | Type | Description |
| :--- | :--- | :--- |
| `Age` | Numerical | Age of the student (18–24 years) |
| `Gender` | Categorical | Gender identity (`Male`, `Female`) |
| `Country` | Categorical | Country of residence |
| `Academic_Level` | Categorical | Current education tier (`High School`, `Undergraduate`, `Graduate`) |
| `Most_Used_Platform` | Categorical | Primary social media platform (e.g., `Instagram`, `Facebook`, `LinkedIn`, `Snapchat`) |
| `Purpose_Of_Use` | Categorical | Primary reason for usage (`Entertainment`, `Networking`, `Education`, etc.) |
| `Avg_Daily_Usage_Hours` | Numerical | Average daily screen time on social media (hours) |
| `Daily_Unlocks` | Numerical | Number of times the smartphone is unlocked per day |
| `Study_Hours` | Numerical | Daily hours dedicated to studying/academics |
| `Physical_Activity_Hours` | Numerical | Daily hours spent on physical exercise/activity |
| `Sleep_Hours_Per_Night` | Numerical | Average nightly sleep duration (hours) |
| `Stress_Level` | Categorical | Self-reported stress tier (`Low`, `Medium`, `High`, `Very High`) |
| **`Mental_Health_Score`** | **Target (Float)** | **Predicted wellness score (ranging from ~3.6 to 9.4)** |

---

## 🛠 Tech Stack

- **Data Analysis & Modeling:** Python, Pandas, NumPy, Matplotlib, Seaborn, Scikit-Learn
- **Backend & API:** FastAPI, Uvicorn, Pydantic, Joblib / Pickle
- **Frontend:** HTML5, CSS3, Vanilla JavaScript (Fetch API)
- **Development Environment:** Jupyter Notebook, VS Code

---

## 📁 Project Architecture & Structure

```text
Mental-Health-Score/
│
├── Student Social Media And Mental Health Impact.csv  # Raw dataset used for training
├── ML_Project.ipynb                                   # EDA, preprocessing, model training & evaluation
├── Mental_Health_Model.pkl                            # Serialized trained ML pipeline/model
│
├── main.py                                            # FastAPI backend server & prediction endpoints
├── requirements.txt                                   # Python dependencies
│
├── index.html                                         # Main frontend web interface
├── style.css                                          # Custom styling and responsive layout
└── script.js                                          # Frontend logic & API integration
```

---

## ⚙️ Machine Learning Pipeline

1. **Data Cleaning & Validation:** Handled anomalous values (e.g., negative physical activity entries) and verified zero missing values across the 5,000 records.
2. **Exploratory Data Analysis (EDA):** Analyzed Pearson correlations and distributions—identifying strong negative correlations between `Avg_Daily_Usage_Hours` / `Daily_Unlocks` and `Mental_Health_Score`, and positive correlations with `Sleep_Hours_Per_Night` and `Physical_Activity_Hours`.
3. **Preprocessing:** Applied `OneHotEncoder` / `OrdinalEncoder` for categorical variables (`Gender`, `Academic_Level`, `Stress_Level`, etc.) and `StandardScaler` for numerical features inside a unified Scikit-Learn `Pipeline` / `ColumnTransformer` to prevent data leakage.
4. **Model Training & Evaluation:** Evaluated multiple regression algorithms (Linear Regression, Random Forest, Gradient Boosting) using $R^2$ Score, Mean Absolute Error (MAE), and Root Mean Squared Error (RMSE), exporting the best-performing model to `Mental_Health_Model.pkl`.

---

## 🚀 Installation & Local Setup

Follow these steps to run the project locally on your machine:

### 1. Clone the Repository
```bash
git clone https://github.com/<your-username>/Mental-Health-Score.git
cd Mental-Health-Score
```

### 2. Create and Activate a Virtual Environment
```bash
# Windows
python -m venv venv
venv\Scripts\activate

# macOS / Linux
python3 -m venv venv
source venv/bin/activate
```

### 3. Install Dependencies
```bash
pip install -r requirements.txt
```

### 4. Start the FastAPI Backend Server
```bash
uvicorn main:app --reload
```
The API will be live at `http://127.0.0.1:8000`. You can explore the interactive API documentation at `http://127.0.0.1:8000/docs`.

### 5. Launch the Frontend
- Ensure the API endpoint URL inside `script.js` points to your local server (`http://127.0.0.1:8000/predict`) or your deployed backend URL.
- Open `index.html` directly in your browser (or use the **Live Server** extension in VS Code).

---

## 🔌 API Usage

### `POST /predict`
Accepts user lifestyle metrics in JSON format and returns the predicted Mental Health Score.

**Sample Request Payload:**
```json
{
  "Age": 21,
  "Gender": "Male",
  "Country": "India",
  "Academic_Level": "Undergraduate",
  "Most_Used_Platform": "Instagram",
  "Purpose_Of_Use": "Entertainment",
  "Avg_Daily_Usage_Hours": 4.5,
  "Daily_Unlocks": 140,
  "Study_Hours": 4.0,
  "Physical_Activity_Hours": 1.5,
  "Sleep_Hours_Per_Night": 7.0,
  "Stress_Level": "Medium"
}
```

**Sample Response:**
```json
{
  "predicted_mental_health_score": 6.84
}
```

---

## 🔮 Future Improvements

- [ ] **Model Explainability:** Integrate **SHAP** (SHapley Additive exPlanations) values to show users *which* specific habits contributed most to their score.
- [ ] **Personalized Recommendations:** Provide actionable wellness tips based on threshold triggers (e.g., high daily unlocks or low sleep hours).
- [ ] **Containerization:** Add a `Dockerfile` and `docker-compose.yml` for one-command deployment across cloud platforms (Render, Railway, AWS).
- [ ] **Unit Testing:** Add `pytest` suites for FastAPI endpoints and data validation schemas.

---

## ⚠️ Disclaimer

*This application is built for educational and analytical purposes only. The predicted Mental Health Score is generated by a statistical model trained on synthetic/survey data and should **not** be used as a substitute for professional medical or psychological diagnosis.*

---

## 🙌 Acknowledgments

- Inspired by the end-to-end Machine Learning tutorial by **Sheryians AI School** (Instructor: *Tanishq Vyas*).
- Dataset sourced from the **Student Social Media and Mental Health Impact** dataset.