# 🚀 MLOps Project: End-to-End Machine Learning Deployment

## 📌 Overview

This project demonstrates an **End-to-End MLOps pipeline** covering **data ingestion, transformation, model training, evaluation, deployment, and CI/CD automation**. It utilizes modern MLOps tools and cloud services like **MongoDB Atlas, AWS, Docker, and GitHub Actions** to ensure seamless model deployment and scaling.

## 📂 Project Structure

```
📦 MLOps_Project
 ┣ 📂 src
 ┃ ┣ 📂 components
 ┃ ┣ 📂 configuration
 ┃ ┣ 📂 entity
 ┃ ┣ 📂 pipeline
 ┃ ┣ 📂 aws_storage
 ┃ ┣ 📂 notebooks
 ┣ 📂 data
 ┣ 📂 templates
 ┣ 📜 setup.py
 ┣ 📜 pyproject.toml
 ┣ 📜 requirements.txt
 ┣ 📜 Dockerfile
 ┣ 📜 .github/workflows/aws.yaml
 ┣ 📜 README.md
```

## 🔧 **Setup and Installation**

### 1️⃣ **Project Initialization**

- Run `template.py` to create a structured project template.
- Add **setup.py** and **pyproject.toml** to manage local packages.

### 2️⃣ **Create & Activate Virtual Environment**

```bash
conda create -n vehicle python=3.10 -y
conda activate vehicle
pip install -r requirements.txt
pip list  # Ensure all packages are installed
```

## 🗄️ **MongoDB Setup**

1. Sign up at [MongoDB Atlas](https://www.mongodb.com/atlas/database)
2. Create a **Cluster** and select the **M0 free tier**.
3. Set up **username/password** and enable **IP Access: 0.0.0.0/0**.
4. Copy the **Connection String** (replace `<password>` with actual password).
5. Load data into MongoDB using **mongoDB\_demo.ipynb**.
6. Verify data in MongoDB Atlas under **Database > Browse Collections**.

## 📝 **Logging, Exception Handling, and EDA**

- Implement **logging.py** and **exception.py** for structured debugging.
- Perform **EDA & Feature Engineering** in Jupyter notebooks.

## 📥 **Data Ingestion**

1. Define **MongoDB connection** in `configuration.mongo_db_connections.py`.
2. Use `data_access/proj1_data.py` to fetch and transform data.
3. Implement `DataIngestionConfig` and `DataIngestionArtifact`.
4. Run `demo.py` (ensure MongoDB URL is set).

**Set MongoDB Connection in Terminal:**

```bash
# Linux/macOS
export MONGODB_URL="mongodb+srv://<username>:<password>@cluster.mongodb.net"

# Windows PowerShell
$env:MONGODB_URL = "mongodb+srv://<username>:<password>@cluster.mongodb.net"
```

## 📊 **Data Validation, Transformation, and Model Training**

- Use `utils.main_utils.py` & `config.schema.yaml` to validate data.
- Implement `DataValidation`, `DataTransformation`, and `ModelTrainer` components.
- Define `estimator.py` in `entity` folder for model training.

## ☁️ **AWS Setup for Model Evaluation & Deployment**

1. **IAM User & S3 Bucket Setup:**
   - Create an **AWS IAM user** with `AdministratorAccess`.
   - Create an **S3 bucket** (`my-model-mlopsproj`).
   - Set **AWS credentials** as environment variables:
   ```bash
   export AWS_ACCESS_KEY_ID="your-access-key"
   export AWS_SECRET_ACCESS_KEY="your-secret-key"
   ```
2. Configure AWS connections in `src.configuration.aws_connection.py`.
3. Implement `s3_estimator.py` for model storage in S3.

## 🚀 **Model Deployment & CI/CD**

### 1️⃣ **Setup CI/CD with Docker & GitHub Actions**

- Configure **Dockerfile** and `.dockerignore`.
- Create **GitHub Actions workflow** in `.github/workflows/aws.yaml`.
- Setup **self-hosted GitHub runner** on AWS EC2.

### 2️⃣ **Deploy on AWS EC2**

- **Create EC2 instance (Ubuntu 24.04, T2 Medium, 30GB storage).**
- **Install Docker on EC2:**
  ```bash
  curl -fsSL https://get.docker.com -o get-docker.sh
  sudo sh get-docker.sh
  sudo usermod -aG docker ubuntu
  newgrp docker
  ```
- **Run self-hosted GitHub runner:**
  ```bash
  ./run.sh  # Start GitHub Runner
  ```

### 3️⃣ **Expose the API**

- Open EC2 **Security Group** > **Edit Inbound Rules** > Add rule:
  - **Type:** Custom TCP
  - **Port:** 5080
  - **Source:** 0.0.0.0/0
- Access the application via:
  ```
  http://<EC2_Public_IP>:5080
  ```

## 🎯 **Final Steps**

- Trigger CI/CD by pushing to GitHub.
- Visit `/training` route for model training.
- Verify deployment and enjoy your **automated MLOps pipeline!** 🚀🎉

---

✅ **Tech Stack Used:** Python, FastAPI, MongoDB, AWS S3, Docker, GitHub Actions, TensorFlow/PyTorch, CI/CD.

🔗 **Let's Connect:** [LinkedIn](https://linkedin.com/in/yashkumar-natholia) | [GitHub](https://github.com/Yashkumar-Natholia)

