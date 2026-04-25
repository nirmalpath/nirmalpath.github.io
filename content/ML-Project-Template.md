# ML Project Template
## Mindmap

## Topics

- Project Structure
- Config
- Data Loading
- Feature Engineering
- Training Pipeline
- Evaluation
- Prediction
- FastAPI
- Main Entry Point
- Requirements
- Dockerfile
- Run Everything
- 

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Project Structure
    ml-project/
    │
    ├── data/
    │   ├── raw/
    │   ├── processed/
    │
    ├── notebooks/
    │   └── eda.ipynb
    │
    ├── src/
    │   ├── __init__.py
    │   ├── config.py
    │   ├── data.py
    │   ├── features.py
    │   ├── train.py
    │   ├── evaluate.py
    │   ├── predict.py
    │
    ├── models/
    │   └── model.pkl
    │
    ├── api/
    │   └── app.py
    │
    ├── tests/
    │
    ├── requirements.txt
    ├── Dockerfile
    ├── README.md
    └── main.py
    
### Config
    # src/config.py
    
    DATA_PATH = "data/processed/data.csv"
    MODEL_PATH = "models/model.pkl"
    
    TARGET = "target"
    TEST_SIZE = 0.2
    RANDOM_STATE = 42

### Data Loading
    # src/data.py
    
    import pandas as pd
    from src.config import DATA_PATH
    
    def load_data():
        return pd.read_csv(DATA_PATH)
    
### Feature Engineering
    # src/features.py
    
    from sklearn.preprocessing import StandardScaler
    
    def preprocess(df, target):
        X = df.drop(target, axis=1)
        y = df[target]
    
        scaler = StandardScaler()
        X_scaled = scaler.fit_transform(X)
    
        return X_scaled, y, scaler

### Training Pipeline
    # src/train.py
    
    from sklearn.model_selection import train_test_split
    from sklearn.ensemble import RandomForestClassifier
    import joblib
    
    from src.config import *
    from src.data import load_data
    from src.features import preprocess
    
    def train():
        df = load_data()
        X, y, scaler = preprocess(df, TARGET)
    
        X_train, X_test, y_train, y_test = train_test_split(
            X, y, test_size=TEST_SIZE, random_state=RANDOM_STATE
        )
    
        model = RandomForestClassifier()
        model.fit(X_train, y_train)
    
        joblib.dump({"model": model, "scaler": scaler}, MODEL_PATH)
    
        return model, X_test, y_test

### Evaluation
    # src/evaluate.py
    
    from sklearn.metrics import accuracy_score
    
    def evaluate(model, X_test, y_test):
        preds = model.predict(X_test)
        acc = accuracy_score(y_test, preds)
        print(f"Accuracy: {acc}")
    
### Prediction
    # src/predict.py
    
    import joblib
    from src.config import MODEL_PATH
    
    artifact = joblib.load(MODEL_PATH)
    
    model = artifact["model"]
    scaler = artifact["scaler"]
    
    def predict(input_data):
        data = scaler.transform([input_data])
        return model.predict(data)[0]
    
### FastAPI
    # api/app.py
    
    from fastapi import FastAPI
    from pydantic import BaseModel
    from src.predict import predict
    
    app = FastAPI()
    
    class Input(BaseModel):
        feature1: float
        feature2: float
        feature3: float
    
    @app.get("/")
    def home():
        return {"message": "ML API is running"}
    
    @app.post("/predict")
    def get_prediction(data: Input):
        result = predict([data.feature1, data.feature2, data.feature3])
        return {"prediction": int(result)}
    
### Main Entry Point
    # main.py
    from src.train import train
    from src.evaluate import evaluate
    
    if __name__ == "__main__":
        model, X_test, y_test = train()
        evaluate(model, X_test, y_test)
    
### Requirements
    pandas
    scikit-learn
    fastapi
    uvicorn
    joblib

### Dockerfile
    FROM python:3.10
    
    WORKDIR /app
    
    COPY . .
    
    RUN pip install -r requirements.txt
    
    CMD ["uvicorn", "api.app:app", "--host", "0.0.0.0", "--port", "8000"]

### Run Everything
    python main.py #train model
    uvicorn api.app:app --reload # run API
