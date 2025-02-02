# Sructure of every ML & DL projects

📂 sensor_fault_detection/   # Root directory
│── 📂 src/                  # Source code folder
│   │── 📂 components/       # Reusable ML/DL components
│   │   │── data_ingestion.py        # Fetches raw data from sources (DB, API, files)
│   │   │── data_preprocessing.py    # Cleans and preprocesses raw data (e.g., missing values, scaling)
│   │   │── model_training.py        # Trains ML/DL models (includes data splitting, training)
│   │   │── model_evaluation.py      # Evaluates models using metrics like accuracy, precision
│   │   │── model_prediction.py      # Makes real-time predictions with trained model
│   │   │── model_registry.py        # Stores and tracks trained models for versioning
│   │   │── model_monitoring.py      # Monitors model performance, alerts for drift or degradation
│   │   │── model_retraining.py      # Retrains the model if performance drops or data drift is detected
│   │── 📂 pipelines/        # ML/DL pipeline management
│   │   │── training_pipeline.py     # Full pipeline from data ingestion to model training
│   │   │── prediction_pipeline.py   # Real-time inference pipeline
│   │   │── monitoring_pipeline.py   # Monitoring pipeline to track and log performance
│   │   │── retraining_pipeline.py   # Retraining pipeline when model accuracy drops
│   │── 📂 config/          # Configuration files for settings and hyperparameters
│   │   │── model_config.yaml        # Hyperparameters, model architecture settings
│   │   │── db_config.yaml           # Database configuration (for fetching/saving data)
│   │   │── hyperparameters.yaml     # Hyperparameter tuning parameters
│   │── 📂 utils/            # Utility functions like logging, configuration reading
│   │   │── logger.py                # Custom logging utility to debug and log events
│   │   │── config_utils.py          # Helper functions to read config files
│   │   │── file_utils.py            # File handling functions (e.g., loading and saving data)
│── 📂 data/                # Dataset storage
│   │── raw/                        # Raw, unprocessed data (e.g., from sensors or APIs)
│   │── processed/                   # Cleaned and preprocessed data ready for modeling
│── 📂 notebooks/           # Jupyter notebooks for experimentation and EDA
│── 📂 artifacts/           # Store trained models, logs, and other output artifacts
│── 📂 logs/                # Logs directory for monitoring and debugging
│   │── mlflow_logs/                    # Logs for experiments tracked by MLFlow
│── 📂 tests/              # Unit tests to verify various modules and components
│   │── test_data_ingestion.py        # Test data ingestion (fetching and loading data)
│   │── test_model_training.py       # Test model training (training and validation)
│   │── test_model_monitoring.py     # Test model monitoring (real-time performance tracking)
│── 📂 deployment/          # Deployment-related files for API and production
│   │── Dockerfile                  # Containerize the application for easy deployment
│   │── requirements.txt            # Lists dependencies to be installed (e.g., FastAPI, TensorFlow)
│   │── app.py                      # FastAPI app for serving the model as an API
│   │── ci_cd/                      # CI/CD configuration files (for automated deployment)
│   │   │── github_actions.yaml     # GitHub Actions workflow for CI/CD pipeline
│── 📂 venv/                 # Virtual environment (hidden directory, not tracked in Git)
│── README.md                # Project documentation (overview, setup, usage)
│── setup.py                 # Setup file for packaging and distribution of the project
│── .gitignore               # Specifies files/folders that should not be tracked in Git
│── .env                     # Environment variables file (for storing sensitive data like API keys)


