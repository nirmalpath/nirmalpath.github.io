# Python Notes
## Mindmap

## Topics

- Basic Syntax

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Load n Explore Data (Pandas)
      import pandas as pd
      
      df = pd.read_csv("data.csv")
      
      print(df.head())
      print(df.info())
      print(df.describe())
      
      # Missing values
      print(df.isnull().sum())
      
### Handling Missing Values
    # Fill with mean
    df["age"].fillna(df["age"].mean(), inplace=True)
    
    # Drop missing
    df.dropna(inplace=True)

### Encode Categorical Values
    from sklearn.preprocessing import LabelEncoder
    
    le = LabelEncoder()
    df["gender"] = le.fit_transform(df["gender"])
    
    ### Feature Scaling
    from sklearn.preprocessing import StandardScaler
    
    scaler = StandardScaler()
    X_scaled = scaler.fit_transform(df[["age", "salary"]])
    

### Train-Test Split
    from sklearn.model_selection import train_test_split
    
    X = df.drop("target", axis=1)
    y = df["target"]
    
    X_train, X_test, y_train, y_test = train_test_split(
        X, y, test_size=0.2, random_state=42
    )

### Train a Model (Classification)
    from sklearn.ensemble import RandomForestClassifier
    
    model = RandomForestClassifier()
    model.fit(X_train, y_train)
    
    preds = model.predict(X_test)

### Evaluate Model
    from sklearn.metrics import accuracy_score, classification_report
    
    print("Accuracy:", accuracy_score(y_test, preds))
    print(classification_report(y_test, preds))
    

### Regression Model
    from sklearn.linear_model import LinearRegression
    
    model = LinearRegression()
    model.fit(X_train, y_train)
    
    preds = model.predict(X_test)

### Hyperparm Tuning
    from sklearn.model_selection import GridSearchCV
    
    params = {"n_estimators": [50, 100], "max_depth": [None, 10]}
    
    grid = GridSearchCV(RandomForestClassifier(), params, cv=3)
    grid.fit(X_train, y_train)
    
    print(grid.best_params_)

### Confusion Matrix
    from sklearn.metrics import confusion_matrix
    
    cm = confusion_matrix(y_test, preds)
    print(cm)

### Feature Importance
    import pandas as pd
    
    importance = model.feature_importances_
    feat_imp = pd.Series(importance, index=X.columns)
    print(feat_imp.sort_values(ascending=False))

### Deep Learning (PyTorch)
    import torch
    import torch.nn as nn
    
    class Net(nn.Module):
        def __init__(self):
            super().__init__()
            self.fc = nn.Linear(10, 1)

        def forward(self, x):
            return self.fc(x)
    
    model = Net()


### Training Loop
    optimizer = torch.optim.Adam(model.parameters(), lr=0.001)
    loss_fn = nn.MSELoss()
    
    for epoch in range(10):
        optimizer.zero_grad()
        output = model(X_train_tensor)
        loss = loss_fn(output, y_train_tensor)
        loss.backward()
        optimizer.step()
    

### NLP/LLM Snippets
#### Basic OpenAPI Call
    from openai import OpenAI
    
    client = OpenAI(api_key="YOUR_API_KEY")
    
    response = client.chat.completions.create(
        model="gpt-4o-mini",
        messages=[{"role": "user", "content": "Explain AI in simple terms"}]
    )
    
    print(response.choices[0].message.content)


#### Simple Text Embeddings
    from openai import OpenAI
    
    client = OpenAI(api_key="YOUR_API_KEY")
    
    emb = client.embeddings.create(
        model="text-embedding-3-small",
        input="AI is transforming the world"
    )
    
    print(emb.data[0].embedding)

#### Semantic Search
    import numpy as np
    
    docs = ["AI is great", "I love pizza", "Machine learning is cool"]
    
    # Assume embeddings generated
    doc_embeddings = [get_embedding(d) for d in docs]
    query_embedding = get_embedding("AI")
    
    # Cosine similarity
    def cosine(a, b):
        return np.dot(a, b) / (np.linalg.norm(a) * np.linalg.norm(b))
    
    scores = [cosine(query_embedding, d) for d in doc_embeddings]
    print(docs[np.argmax(scores)])


### Plot Data
    import matplotlib.pyplot as plt
    
    plt.plot([1,2,3], [4,5,6])
    plt.xlabel("X")
    plt.ylabel("Y")
    plt.show()

### Pipeline (Clean + Model)
    from sklearn.pipeline import Pipeline
    
    pipeline = Pipeline([
        ("scaler", StandardScaler()),
        ("model", RandomForestClassifier())
    ])
    
    pipeline.fit(X_train, y_train)

### Save n Load Model
    import joblib
    
    joblib.dump(model, "model.pkl")
    model = joblib.load("model.pkl")

### Cross Validation
    from sklearn.model_selection import cross_val_score
    
    scores = cross_val_score(model, X, y, cv=5)
    print(scores.mean())
