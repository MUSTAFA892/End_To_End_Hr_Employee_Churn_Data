
---

# End_To_End_Hr_Employee_Churn_Data


## Overview

This project predicts employee churn rate using machine learning models, including KMeans clustering and XGBoost. It is structured using modular programming principles to ensure a clean and scalable workflow. The project includes data ingestion, preprocessing, training, prediction, and model tuning, all within a Flask application.

## Project Structure

The project directory is organized as follows:

```
.
├── Datasets/
│   └── hr_employee_churn_data.csv
├── apps/
│   ├── core/
│   ├── training/
│   ├── prediction/
│   └── preprocess/
├── config.py
├── file_operation.py
├── logger.py
├── database/
│   ├── columns.json
│   ├── database_operation.py
│   ├── schema_predict.json
│   ├── schema_train.json
│   └── training.db
├── ingestion/
│   └── load_validate.py
├── models/
│   ├── KMeans/
│   ├── XGBoost0/
│   ├── XGBoost1/
│   ├── XGBoost2/
│   └── kmeans_elbow.png
├── tuning/
│   ├── cluster.py
│   └── model_tuner.py
├── data/
│   ├── training_data/
│   ├── prediction_data/
│   └── .gitkeep
├── logs/
│   ├── prediction_logs/
│   └── training_logs/
├── templates/
│   └── index.html
├── .gitignore
├── main.py
├── requirements.txt
└── flask_monitoringdashboard.db
```

## Requirements

Before running the project, you need to install the required dependencies. You can do this by running the following command:

```bash
pip install -r requirements.txt
```

The `requirements.txt` includes:

```
Flask
Flask-Cors
matplotlib
numpy
pandas
scikit-learn
kneed
xgboost
Flask-MonitoringDashboard
Jinja2
Werkzeug
itsdangerous
certifi
MarkupSafe
```

## Running the Flask Application

To run the Flask application, follow these steps:

1. **Start the Flask application**: Run the following command in your terminal:

```bash
python main.py
```

2. **Access the application**: The Flask app will be running on `http://localhost:5000`. You should see the index page where you can interact with the models.

3. **Training the Model**: To train the model, you can use Postman or Thunder Client to send a `POST` request to the following endpoint:

```
POST http://localhost:5000/training
```

This will trigger the model training process. Once training is complete, you will receive a response containing the training run ID and a success message.

4. **Making Predictions**:
   - **Single Prediction**: You can make a single prediction by sending a `POST` request to the following endpoint:

     ```
     POST http://localhost:5000/prediction
     ```

     In the body of the request, provide the following parameters:

     - `satisfaction_level`
     - `last_evaluation`
     - `number_project`
     - `average_montly_hours`
     - `time_spend_company`
     - `work_accident`
     - `promotion_last_5years`
     - `salary`

     Example body (form-data):
     ```
     satisfaction_level: 0.7
     last_evaluation: 0.8
     number_project: 5
     average_montly_hours: 150
     time_spend_company: 3
     work_accident: 0
     promotion_last_5years: 0
     salary: high
     ```

     This will return the predicted churn outcome.

   - **Batch Prediction**: You can also make batch predictions by sending a `POST` request to:

     ```
     POST http://localhost:5000/batchprediction
     ```

     This will return the prediction for multiple data points as a batch.

5. **Accessing the GUI**: After launching the app, you can visit the root URL (`/`) in your browser. This will display a graphical user interface where you can interact with the model and make predictions.

## Contributing

Feel free to fork this repository, create an issue, or submit a pull request for any bug fixes, improvements, or additional features.

---

This `README.md` should provide clear instructions on setting up and using your project while also offering a description of the folder structure and key components involved in the churn prediction pipeline.