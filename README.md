
<div align="center">

# NYC Airbnb Room Type Predictor

### Machine Learning-Based Room Type Classification System

An end-to-end Machine Learning project that predicts the room type of New York City Airbnb listings using listing characteristics such as location, price, availability, reviews, and host information.

[![Python](https://img.shields.io/badge/Python-3.12-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![Scikit-learn](https://img.shields.io/badge/Scikit--learn-Machine_Learning-F7931E?style=for-the-badge&logo=scikitlearn&logoColor=white)](https://scikit-learn.org/)
[![FastAPI](https://img.shields.io/badge/FastAPI-Backend-009688?style=for-the-badge&logo=fastapi&logoColor=white)](https://fastapi.tiangolo.com/)
[![Pandas](https://img.shields.io/badge/Pandas-Data_Analysis-150458?style=for-the-badge&logo=pandas&logoColor=white)](https://pandas.pydata.org/)
[![JavaScript](https://img.shields.io/badge/JavaScript-Frontend-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)](https://developer.mozilla.org/en-US/docs/Web/JavaScript)

---

**Analyze Airbnb Listings. Predict Room Types. Turn Data into Insights.**

</div>

---

## The Problem

New York City has thousands of Airbnb listings with different locations, prices, availability, and accommodation types.

Identifying whether a listing is an entire home, private room, or shared room based on its characteristics is a machine learning classification problem.

## The Solution

The **NYC Airbnb Room Type Predictor** uses machine learning to classify Airbnb listings into three categories:

- Entire home/apt
- Private room
- Shared room

The project follows an end-to-end machine learning workflow, from exploratory data analysis and preprocessing to model training, evaluation, and deployment through a FastAPI backend.

Users can enter listing details through an interactive web interface and receive a predicted room type with probability values.

---

## Features

| Feature | Description |
|---|---|
| Exploratory Data Analysis | Analyze distributions, missing values, correlations, and outliers |
| Data Preprocessing | Handle missing values, scale numerical features, and encode categorical features |
| Feature Engineering | Prepare numerical and categorical input features |
| Model Comparison | Compare multiple classification algorithms |
| Hyperparameter Tuning | Optimize the Random Forest classifier using RandomizedSearchCV |
| Model Evaluation | Evaluate using Accuracy, Macro F1-score, and Confusion Matrix |
| Model Serialization | Save the complete ML pipeline using Joblib |
| Room Type Prediction | Generate predictions through FastAPI |
| Probability Output | Return prediction probabilities for each room type |
| Interactive Web Interface | Enter listing details and view prediction results |

---

## System Architecture

The following diagram illustrates the complete machine learning and prediction workflow.

![NYC Airbnb System Architecture](System%20architecture.png)

### Architecture Workflow

1. **Dataset:** Load NYC Airbnb listing data from Kaggle.
2. **Data Preprocessing:** Handle missing values, scale numerical features, and encode categorical features.
3. **Model Training:** Train and compare classification algorithms.
4. **Model Evaluation:** Evaluate models using Accuracy and Macro F1-score.
5. **Best Model Selection:** Perform hyperparameter tuning on the Random Forest classifier.
6. **Model Storage:** Save the complete preprocessing and trained model pipeline.
7. **Frontend:** Collect listing details from users.
8. **FastAPI Backend:** Validate input and generate predictions using the saved model.
9. **Output:** Display the predicted room type and probability values.

---

## Model Performance

The final model was evaluated on the held-out test dataset.

| Evaluation Metric | Score |
|---|---:|
| Accuracy | **85.70%** |
| Macro F1-score | **74.18%** |

Macro F1-score is useful for evaluating performance across all room-type categories, especially when class distributions are imbalanced.

---

## Tech Stack

| Category | Technology |
|---|---|
| Programming Language | Python |
| Data Manipulation | NumPy, Pandas |
| Data Visualization | Matplotlib, Seaborn |
| Machine Learning | Scikit-learn |
| Model Serialization | Joblib |
| Backend Framework | FastAPI |
| API Server | Uvicorn |
| Data Validation | Pydantic |
| Frontend | HTML5, CSS3, JavaScript |
| Dataset | NYC Airbnb Open Data |

---

## Project Structure

```text
Project1_NYC_Airbnb/
│
├── NYC_Airbnb.ipynb
│   └── EDA, preprocessing, model training and evaluation
│
├── Model_Pipeline.pkl
│   └── Saved preprocessing and trained model pipeline
│
├── main.py
│   └── FastAPI application and prediction API
│
├── frontend/
│   ├── index.html
│   ├── style.css
│   └── script.js
│
├── System architecture.png
│   └── System architecture diagram
│
├── requirements.txt
├── runtime.txt
└── README.md
```

---

## Getting Started

### 1. Clone the Repository

```bash
git clone https://github.com/diyapandya/Project1_NYC_Airbnb.git

cd Project1_NYC_Airbnb
```

### 2. Create a Virtual Environment

```bash
python -m venv venv
```

### 3. Activate the Environment

**Windows PowerShell:**

```powershell
.\venv\Scripts\Activate.ps1
```

**Linux / macOS:**

```bash
source venv/bin/activate
```

### 4. Install Dependencies

```bash
pip install -r requirements.txt
```

### 5. Run the Application

```bash
uvicorn main:app --reload
```

### 6. Open the Application

Visit:

```text
http://127.0.0.1:8000
```

FastAPI automatically serves the frontend through the application.

**API Documentation:**

```text
http://127.0.0.1:8000/docs
```

---

## Machine Learning Workflow

The project follows a complete machine learning lifecycle:

1. **Data Loading:** Download the NYC Airbnb dataset using KaggleHub.
2. **Exploratory Data Analysis:** Analyze missing values, distributions, correlations, skewness, and outliers.
3. **Data Cleaning:** Prepare the dataset for model development.
4. **Train-Test Split:** Split the data with stratification to maintain class proportions.
5. **Preprocessing:**
   - Numerical features: Median imputation and StandardScaler.
   - Categorical features: Most-frequent imputation and OneHotEncoder.
6. **Model Training:** Train Logistic Regression, Decision Tree, Random Forest, and Gradient Boosting.
7. **Model Comparison:** Compare classification models using cross-validation.
8. **Hyperparameter Tuning:** Apply RandomizedSearchCV with 3-fold cross-validation and Macro F1 scoring.
9. **Final Evaluation:** Evaluate the selected model on unseen test data.
10. **Model Saving:** Serialize the complete pipeline using Joblib.
11. **Deployment:** Integrate the saved model with FastAPI and the frontend.

---

## API Reference

### POST `/predict`

Accepts listing details and returns the predicted room type along with class probabilities.

**Input Features:**

| Feature | Description |
|---|---|
| `latitude` | Listing latitude |
| `longitude` | Listing longitude |
| `price` | Price per night |
| `minimum_nights` | Minimum nights required |
| `number_of_reviews` | Total reviews |
| `reviews_per_month` | Average monthly reviews |
| `calculated_host_listings_count` | Host listing count |
| `availability_365` | Annual availability |
| `neighbourhood_group` | NYC borough |
| `neighbourhood` | Specific neighbourhood |

**Example Response:**

```json
{
  "Predicted_room_type": "Private room",
  "Probability": [
    0.25,
    0.65,
    0.10
  ]
}
```

*The probability values above are illustrative. Actual values depend on the listing details and trained model.*

---

## Dataset

**New York City Airbnb Open Data**

The project uses the **AB_NYC_2019** dataset containing Airbnb listing information, including location, price, room type, reviews, and availability.

**Dataset Source:**

[New York City Airbnb Open Data – Kaggle](https://www.kaggle.com/datasets/dgomonov/new-york-city-airbnb-open-data)

The notebook downloads the dataset using KaggleHub.

---

## Developer

Connect with the project developer:

[![GitHub](https://img.shields.io/badge/GitHub-Profile-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/diyapandya)

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Profile-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/diya-pandya-399b382b1/)

---

## License

This project is developed for educational and learning purposes.

---

<div align="center">

**NYC Airbnb Room Type Predictor — Turning Listing Data into Machine Learning Predictions.**

</div>
