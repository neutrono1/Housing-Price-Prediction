# Housing Price Prediction

This project predicts median house values in California using the **California Housing Prices** dataset from Kaggle.

###  Dataset Link
Dataset used: https://www.kaggle.com/datasets/camnugent/california-housing-prices

---

## Model Performance (Cross‑Validation RMSE)

### **1. Linear Regression RMSE**
```
count       10.000000
mean     69204.322755
std       2500.382157
min      65318.224029
25%      67124.346106
50%      69404.658178
75%      70697.800632
max      73003.752739
dtype: float64
```

### **2. Decision Tree Regressor RMSE**
```
count       10.000000
mean     69081.361563
std       2420.500173
min      64770.563939
25%      67525.053996
50%      69027.994020
75%      70675.556581
max      73280.387324
dtype: float64
```

### **3. Random Forest Regressor RMSE**
```
count       10.000000
mean     50511.703557
std       2341.932302
min      46567.496518
25%      48618.159666
50%      50665.960872
75%      52207.889026
max      53608.491010
dtype: float64
```
 **Random Forest performed the best and was selected as the final model.**

---

##  Project Workflow

###  **Training Phase**
- Load `housing.csv`
- Create stratified train-test split using `median_income`
- Build preprocessing pipeline:
  - Numerical: imputation + scaling
  - Categorical: one-hot encoding
- Train **RandomForestRegressor**
- Save model & pipeline using `joblib`

###  **Inference Phase**
- Load saved model and pipeline
- Read `input.csv` (auto-generated during training)
- Transform input data
- Predict median house values
- Save predictions into `output.csv`

---

##  **Project Structure**
```
├── main.py
├── readme.md
├── housing.csv
├── Visualizingthedata


```

---



##  Installation & Environment Setup

Before running the project on a new laptop/machine, you must install the required Python packages.

###  **1. Create a Virtual Environment (Recommended)**
```
python -m venv env
```
Activate it:
- **Windows:**
```
env\Scripts\activate
```
- **macOS/Linux:**
```
source env/bin/activate
```

###  **2. Install Required Modules**
Run:
```
pip install -r requirements.txt
```

Or install manually:
```
pip install numpy pandas scikit-learn joblib
```

###  requirements.txt (Add this file)
```
numpy
pandas
scikit-learn
joblib
```

---

##  How to Run

###  Train Model
```
python main.py
```
- Trains the Random Forest model
- Saves `model.pkl` and `pipeline.pkl`
- Generates `input.csv` (test data)

### Run Inference
```
python main.py
```
- Loads saved model
- Predicts values for `input.csv`
- Saves output to `output.csv`

---

##  Conclusion
- Random Forest gave the best RMSE scores
- Full pipeline automation: preprocessing → training → prediction
- Easy to extend for deployment or API usage

