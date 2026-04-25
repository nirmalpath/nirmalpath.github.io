# Python Numpy n Pandas Tricks
## Topics
### Pandas
- Query instead of filtering
- Assign new columns inline (no temp variables)
- Use map for fast value replacement
- GroupBy + multiple aggregations
- Sort within groups
- Vectorized Conditional Logic (no loops)
- Rank within groups
- Drop duplicates but keep latest
- Pivot Tables
- Explode lists into rows
- Find top N per group
- Fast row-wise operations (avoid apply)
- Rolling Window (time series)
- Shift for lag features
- Efficient String Operations

### Numpy
- Broadcasting (no loops)
- Boolean Masking
- Vectorized Math (super fast)
- Where with arrays
- Stack Arrays
- Reshape like pro
- Argmax/min
- Random Sampling
- Normalize Data
- Efficient Filtering with Multiple Conditions

### Combined Tricks
- Fast conditional column creation
- Covert DataFrame to Numpy (speed boost)
- Apply NumPy functions on Dataframe
- Correlation Matrix
- Memory Optimization

-------------------------------------------------------------------Details-------------------------------------------------------------------------------------------------------------------------
### Pandas
#### Query instead of filtering
    df.query("age > 30 and salary < 50000")

#### Assign new columns inline (no temp variables)
    df = df.assign(
        income_per_age = df["salary"] / df["age"]
    )

#### Use map for fast value replacement
    df["gender"] = df["gender"].map({"M": 0, "F": 1})

#### GroupBy + multiple aggregations
    df.groupby("department").agg({
        "salary": ["mean", "max"],
        "age": "min"
    })

#### Sort within groups
    df.sort_values(["department", "salary"], ascending=[True, False])

#### Vectorized Conditional Logic (no loops)
    import numpy as np
    
    df["bonus"] = np.where(df["salary"] > 50000, 1000, 500)

#### Rank within groups
    df["rank"] = df.groupby("department")["salary"].rank(ascending=False)

#### Drop duplicates but keep latest
    df = df.sort_values("date").drop_duplicates("user_id", keep="last")

#### Pivot Tables
    df.pivot_table(
        values="salary",
        index="department",
        columns="gender",
        aggfunc="mean"
    )

#### Explode lists into rows
    df.explode("tags")

#### Find top N per group
    df.groupby("department").head(3)

#### Fast row-wise operations (avoid apply)
    # BAD (slow)
    df["z"] = df.apply(lambda x: x["a"] + x["b"], axis=1)
    
    # GOOD (fast)
    df["z"] = df["a"] + df["b"]
    
#### Rolling Window (time series)
    df["rolling_avg"] = df["sales"].rolling(window=7).mean()

#### Shift for lag features
    df["prev_day_sales"] = df["sales"].shift(1)

#### Efficient String Operations
    df["name"] = df["name"].str.lower().str.strip()

### Numpy
#### Broadcasting (no loops)
    import numpy as np
    
    arr = np.array([1, 2, 3])
    result = arr * 10

#### Boolean Masking
    arr[arr > 2]

#### Vectorized Math (super fast)
    np.sqrt(arr)
    np.log(arr)

#### Where with arrays
    np.where(arr > 2, "High", "Low")

#### Stack Arrays
    np.vstack([arr, arr])
    np.hstack([arr, arr])

#### Reshape like pro
    arr.reshape(3, 1)

#### Argmax/min
    np.argmax(arr)
    np.argmin(arr)

#### Random Sampling
    np.random.choice(arr, size=2, replace=False)

#### Normalize Data
    (arr - arr.mean()) / arr.std()

#### Efficient Filtering with Multiple Conditions
    arr[(arr > 1) & (arr < 3)]

### Combined Tricks
#### Fast conditional column creation
        df["category"] = np.select(
          [
              df["salary"] > 70000,
              df["salary"] > 40000
          ],
          ["High", "Medium"],
          default="Low"
        )

#### Covert DataFrame to Numpy (speed boost)
      arr = df.values

#### Apply NumPy functions on Dataframe
    df["log_salary"] = np.log(df["salary"])

#### Correlation Matrix
    df.corr(numeric_only=True)

#### Memory Optimization
    df["col"] = df["col"].astype("int32")
