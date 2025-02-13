
# Spark MLOps Fundamentals -  Demo

## Purpose
This project serves as a small demo to showcase **Spark** for data processing, **MLOps** practices, and **CI/CD** integration (using Jenkins) on a simple machine learning workflow.

## Tools Used
- **PySpark** for ETL and data transformations
- **MLFlow** for experiment tracking and model versioning
- **Jenkins** for CI/CD pipeline automation
- **Local Hadoop/Spark** to simulate distributed computing
- **Azure** for cloud storage
- **Git** & **GitHub** for source control

---

## Data: Titanic Dataset

- **Source**: [Kaggle’s Titanic competition](https://www.kaggle.com/competitions/titanic)  
- **Features**: `PassengerId, Name, Age, Sex, Pclass, Fare, Survived`, etc.  
- **Goal**: Predict survival (0 or 1) based on passenger attributes.  
- **Usage**:
  - You can place a local copy in `data/titanic.csv`,
  - or **download** it from a **cloud source** (e.g., Azure Blob Storage) in the ETL notebook.

---

## ETL: `pyspark_etl.ipynb`

**Location**: `notebooks/pyspark_etl.ipynb`  
**Purpose**:  
1. **Initialize Spark** in local mode.  
2. **Fetch** the Titanic CSV from local or cloud (Azure).  
3. **Clean** data (drop nulls, parse columns, etc.).  
4. **Explore** data with Spark SQL.  

**Key Steps**:
- `spark.read.csv(...)` loads the CSV into a Spark DataFrame.  
- `df.dropna(...)` removes rows with missing values.  
- Spark SQL queries can be run after `df.createOrReplaceTempView("titanic")`.  
- The final cleaned DataFrame can be saved or passed on for modeling.

---

## Modeling: `ml_training.ipynb`

**Location**: `notebooks/ml_training.ipynb`  
**Purpose**:  
1. **Load** the cleaned Titanic data (from local or from the ETL step).  
2. **Feature Engineering**: Convert string columns to numeric, assemble features.  
3. **Train** a simple **Logistic Regression** or other classifier with PySpark MLlib.  
4. **Evaluate** performance (accuracy, AUC).  
5. **(Optional) MLFlow**: Log metrics (AUC, parameters) and model artifacts.

**Key Steps**:
- `StringIndexer` encodes categorical features.  
- `VectorAssembler` merges features into a single vector column.  
- `LogisticRegression` trains the classifier.  
- A **BinaryClassificationEvaluator** computes AUC.  
- `mlflow.start_run(...)` + `mlflow.log_metric(...)` optionally tracks metrics.

---

## How to Use
1. Clone this repo: `git clone https://github.com/<your-username>/spark-mlops-demo.git`
2. Install dependencies: (PySpark, MLFlow, etc.).
4. Run Jupyter notebooks in the `notebooks/` folder to see the code and steps in action.

---

## CI/CD with GitHub Actions

This project uses GitHub Actions to automatically:
1. Check out the code
2. Install Python dependencies (PySpark, MLflow, etc.)
3. Run notebooks or tests in headless mode
4. Provide pass/fail feedback on each commit

See the [Actions](../../actions) tab for build logs.

---

## Future Improvements
- Unit Tests: Add PyTest tests for data transformations or model code.
- Docker: Containerize the environment for reproducible runs in CI and local machines.
- Remote MLFlow: Host MLFlow artifacts in a cloud bucket (AWS S3 or Azure Blob).
- Deployment: Package the final model into a REST API (e.g., FastAPI) or serverless function.
