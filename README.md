# Brazilian E-commerce Analysis with Spark and MLflow

This project demonstrates an end-to-end Machine Learning workflow using Apache Spark for data processing and clustering, and MLflow for experiment tracking and model management. It uses the [Brazilian E-Commerce Public Dataset by Olist](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce).

## Project Overview

The notebook performs the following steps:

1.  **Data Ingestion**: Downloads the dataset using `kagglehub` and loads multiple CSV files (orders, customers, products, etc.) into Spark DataFrames.
2.  **ETL & Feature Engineering**:
    *   Joins multiple DataFrames to create a comprehensive view of each order.
    *   Cleans data by handling missing values and converting data types (e.g., timestamps).
    *   Creates new features such as `order_duration_days`.
3.  **Machine Learning**:
    *   Prepares numerical features using `VectorAssembler`.
    *   Trains a K-Means clustering model (`k=3`) to segment orders/customers.
    *   Evaluates the model using the Silhouette score.
4.  **Experiment Tracking**:
    *   Logs the experiment runs using **MLflow**.
    *   Tracks parameters (input columns, k), metrics (Silhouette score), and the trained model.
    *   Registers the model in the MLflow Model Registry.
    *   Sets up a tunnel using `ngrok` to access the MLflow UI (useful for remote environments like Colab).

## Prerequisites

*   Python 3.7+
*   Apache Spark (PySpark)
*   Java 8/11 (required for Spark)
*   Kaggle account (for dataset download)

## Dependencies

The following Python libraries are used:

*   `pyspark`
*   `mlflow`
*   `kagglehub`
*   `pyngrok` (for exposing MLflow UI)

## Setup and Usage

1.  **Clone the repository** (if applicable) or download the notebook.

2.  **Install Dependencies**:
    ```bash
    pip install pyspark mlflow kagglehub pyngrok
    ```

3.  **Run the Notebook**:
    Open `spark+mlflow (1).ipynb` in Jupyter Notebook, JupyterLab, or Google Colab.

4.  **Execute Cells**:
    Run the cells sequentially. The notebook will:
    *   Download the dataset automatically.
    *   Process the data.
    *   Train the model.
    *   Start the MLflow tracking server.

5.  **Access MLflow UI**:
    The final steps of the notebook set up `ngrok` to tunnel the MLflow UI. Look for the output:
    ```
    MLflow UI Tunnel URL: ...
    ```
    Click the link to view your experiment runs and registered models.

## Key Features Used

*   **Spark SQL**: For efficient data joining and transformation.
*   **Spark MLlib**: For feature vectorization (`VectorAssembler`) and clustering (`KMeans`).
*   **MLflow Tracking**: To log parameters, metrics, and artifacts.
*   **MLflow Model Registry**: To version and manage the trained models.
