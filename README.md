Here’s an overview of the project structure:
```
ci-cd-ml-project/
├── prediction_model/
│   ├── config/
│   │   ├── __init__.py
│   │   ├── config.py
│   ├── datasets/
│   │   ├── __init__.py
│   │   ├── loan_approval_dataset.csv
│   │   ├── test_data_features.csv
│   │   ├── test_data_target.csv
│   │   └── test_data.csv
│   ├── processing/
│   │   ├── __init__.py
│   │   ├── data_handling.py
│   │   └── preprocessing.py
│   ├── trained_models/
│   │   ├── __init__.py
│   └── pipeline.py
│   └── predict.py
│   └── training_pipeline.py
│   └── VERSION
├── tests/
│   ├── pytest.ini
│   └── test_prediction.py
├── .gitignore
├── Dockerfile
├── MANIFEST.in
├── README.md
├── requirements.txt
├── setup.py
└── main.py
```

# Setup Virtual Environment

```python
conda create -n fastapi-env python=3.10
conda activate fastapi-env
pip install -r requirements.txt
```

# Running the server
`uvicorn main:app --reload`
# `uvicorn main:my_first_api --reload`

The command `uvicorn main:app` refers to:
- main: the file main.py (the Python "module").
- app: the object created inside of main.py with the line app = FastAPI().
- --reload: make the server restart after code changes. Only use for development.


```json
Yes

```

```bash
curl -X 'POST' \
  'http://127.0.0.1:8005/predict' \
  -H 'accept: application/json' \
  -H 'Content-Type: application/json' \
  -d '{
  "Dependents": 2,
  "Education": "Graduate",
  "Self_Employed": "Yes",
  "TotalIncome": 110,
  "LoanAmount": 220,
  "Loan_Amount_Term": 220,
  "Credit_History": 220,
  "Residential_Assets_Value": 110,
  "Commercial_Assets_Value": 110,
  "Luxury_Assets_Value": 110,
  "Bank_Asset_Value": 110
}'

```

# ci-cd-python - Commands to install Docker on EC2 
- Ensure port 80 is available
```
sudo yum update -y
sudo amazon-linux-extras install docker -y
sudo service docker start
sudo systemctl start docker
sudo service docker status
sudo groupadd docker
sudo usermod -a -G docker ec2-user
newgrp docker
docker —-version

# create ECR with name: my-mlapp
aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin 866824485776.dkr.ecr.us-east-1.amazonaws.com
```
```
Explanation of Each Folder and File
prediction_model/
config/: Contains configuration files, such as config.py, which typically stores project settings, parameters, and file paths to manage different environments and configurations. The __init__.py file allows this folder to be treated as a module.

datasets/: Contains the dataset files, including loan_approval_dataset.csv and various test data files (test_data_features.csv, test_data_target.csv, etc.) used for validation and testing.

processing/: Houses the scripts for data preprocessing and data handling.

data_handling.py and preprocessing.py likely contain functions for cleaning, transforming, and preparing data for training and prediction.
The __init__.py file allows these files to be imported as modules.
trained_models/: Intended to store trained model files. The __init__.py indicates it is a module. Avoid storing large model files here if possible. For MLOps, consider using a model registry (e.g., MLflow or S3) for model storage and management.

pipeline.py: Likely defines the machine learning pipeline, combining different stages such as data preprocessing and model training into one cohesive process.

predict.py: Likely handles predictions by loading a trained model and performing inference on new data.

training_pipeline.py: The main script for training models, executing all stages of the model training process, including data processing, model selection, and training.

VERSION: Stores the version of the current model. Versioning is essential in MLOps for tracking changes and supporting model management.

tests/
Contains the test suite for the project, which includes:

pytest.ini: Configuration file for running tests with pytest.
test_prediction.py: Script for validating the prediction process, ensuring the models perform as expected.
```
```
Root-Level Files
Dockerfile: Defines the environment to run the application, enabling consistent setup across different stages such as development, testing, and production.

MANIFEST.in: Lists files that should be included in the package distribution, such as configuration files or datasets.

README.md: Provides documentation and an overview of the project, including installation, usage, and other relevant details.

requirements.txt: Lists the dependencies required for the project. This file is used to set up environments with the necessary packages, especially useful in CI/CD pipelines.

setup.py: The setup script for packaging and distributing the project as a Python package.

main.py: Likely serves as the main entry point for running the application.

```
