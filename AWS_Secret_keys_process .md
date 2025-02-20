🔹 Step 1: Store AWS Keys in GitHub Secrets
~~~
Go to your GitHub repository.
Click on Settings.
In the left sidebar, go to Secrets and variables → Actions.
Click New repository secret (button in the top-right).
Add the following secrets:
Name: AWS_ACCESS_KEY_ID

Value: (your AWS access key)

Click Add secret

Name: AWS_SECRET_ACCESS_KEY

Value: (your AWS secret key)

Click Add secret
~~~
🔹 Step 2: Create a GitHub Actions Workflow
Now, we need to create a GitHub Actions workflow that will load these secrets when running your Python code.

1. Create Workflow File
Inside your repository, navigate to:
~~~
Edit
.github/workflows/
If the folder doesn't exist, create it.
Inside .github/workflows/, create a new file called deploy.yml.
2. Add This Code to deploy.yml
yaml
Copy
Edit
name: Deploy AWS Script

on:
  push:
    branches:
      - main  # Runs when pushing to the main branch

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout repository
        uses: actions/checkout@v3

      - name: Set up Python
        uses: actions/setup-python@v4
        with:
          python-version: '3.9'

      - name: Install dependencies
        run: pip install -r requirements.txt

      - name: Run Python script with AWS credentials
        env:
          AWS_ACCESS_KEY_ID: ${{ secrets.AWS_ACCESS_KEY_ID }}
          AWS_SECRET_ACCESS_KEY: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
        run: python app.py
🔹 What this does:

Pulls the latest code from your GitHub repo.
Sets up Python.
Installs dependencies.
Exposes AWS credentials as environment variables.
Runs your Python script (app.py).

~~~
🔹 Step 3: Modify Your Python Code
Now, modify your Python script (app.py) to use these environment variables.

1. Import Required Libraries

Edit
import os
import boto3
2. Fetch AWS Credentials Securely

Edit
# Load AWS credentials from environment variables
aws_access_key = os.getenv("AWS_ACCESS_KEY_ID")
aws_secret_key = os.getenv("AWS_SECRET_ACCESS_KEY")

if not aws_access_key or not aws_secret_key:
    raise ValueError("AWS credentials not found. Make sure they are set as environment variables.")
3. Use AWS SDK (Example: List S3 Buckets)

~~~
# Initialize AWS S3 client
s3_client = boto3.client(
    "s3",
    aws_access_key_id=aws_access_key,
    aws_secret_access_key=aws_secret_key
)

# List all S3 buckets
buckets = s3_client.list_buckets()

print("AWS S3 Buckets:")
for bucket in buckets['Buckets']:
    print(f"- {bucket['Name']}")
~~~

🔹 Step 4: Commit & Push Your Code
Once you've set up everything:

Add and commit your changes:

~~~
git add .
git commit -m "Added AWS credentials via GitHub Secrets"
git push origin main
~~~
Trigger GitHub Actions Workflow

Once you push the code, GitHub Actions will run the workflow (deploy.yml).
It will load AWS credentials, execute app.py, and list AWS S3 buckets.
