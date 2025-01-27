
# Spark MLOps Demo

## Purpose
This project serves as a small demo to showcase **Spark** for data processing, **MLOps** practices, and **CI/CD** integration (using Jenkins) on a simple machine learning workflow.

## Tools Used
- **PySpark** for ETL and data transformations
- **MLFlow** for experiment tracking and model versioning
- **Jenkins** for CI/CD pipeline automation
- **Local Hadoop/Spark** to simulate distributed computing
- **Azure** for cloud storage
- **Git** & **GitHub** for source control

## Project Flow
1. **Data Acquisition**: Fetch data from a public source or cloud storage (Azure Blob/GCP Bucket).
2. **Data Processing**: Use PySpark to clean and transform the data.
3. **Model Training**: Train a simple ML model (e.g., classification or regression).
4. **Experiment Tracking**: Log parameters and metrics in MLFlow.
5. **CI/CD**: Jenkins pipeline to automate testing and ensure stable builds.
6. **Deployment** (Optional): Package the final model or push it to a model registry.

## How to Use
1. Clone this repo: `git clone https://github.com/<your-username>/spark-mlops-demo.git`
2. Install dependencies (PySpark, MLFlow, etc.). 'pip install -r requirements.txt
'
3. Run Jupyter notebooks in the ` notebooks/` folder to see the code and steps in action.
4. Open pyspark_etl.ipynb or ml_training.ipynb and run the cells.
5. If you want to see MLflow logs:  ` mlflow ui'
6. 


