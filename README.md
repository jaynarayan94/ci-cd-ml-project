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
