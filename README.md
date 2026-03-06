Dockerized Web Application Deployment on AWS EC2

1)Project Overview:

This project demonstrates how to containerize a Python web application using Docker and deploy it on an AWS EC2 instance.

The application is built using Flask, packaged into a Docker container, and hosted on a cloud server so it can be accessed publicly through the EC2 public IP address.

This project showcases practical skills in:

Cloud Computing

Docker Containerization

Linux Server Management

AWS EC2 Deployment

GitHub Version Control

2)Architecture:

Developer
   │
   ▼
GitHub Repository
   │
   ▼
AWS EC2 Instance (Ubuntu)
   │
   ▼
Docker Container
   │
   ▼
Flask Web Application

3)Technologies Used

AWS EC2 (Free Tier)

Docker

Python

Flask

Linux (Ubuntu Server)

Git & GitHub

4)Project Structure
docker-aws-cicd-project
│
├── app.py
├── requirements.txt
├── Dockerfile
└── README.md

5)Application Code
app.py
from flask import Flask

app = Flask(__name__)

@app.route("/")
def home():
    return "Hello! This app is running inside Docker on AWS EC2."

if __name__ == "__main__":
    app.run(host="0.0.0.0", port=5000)
📦 Dockerfile
FROM python:3.9

WORKDIR /app

COPY requirements.txt .

RUN pip install -r requirements.txt

COPY . .

CMD ["python", "app.py"]
📜 requirements.txt
flask
⚙️ Deployment Steps
1️⃣ Launch AWS EC2 Instance

Instance Type: t2.micro (Free Tier)

OS: Ubuntu

Security Group Ports:

22  → SSH
80  → HTTP

2️⃣ Connect to EC2 Server
ssh -i key.pem ubuntu@PUBLIC_IP

3️⃣ Install Docker
sudo apt update
sudo apt install docker.io -y

4️⃣ Clone GitHub Repository
git clone https://github.com/MadhanRajG1/docker-aws-cicd-project.git
cd docker-aws-cicd-project

5️⃣ Build Docker Image
sudo docker build -t flask-app .

6️⃣ Run Docker Container
sudo docker run -d -p 80:5000 flask-app

7️⃣ Access Application

Open browser:

http://EC2_PUBLIC_IP

You should see:


Hello! This app is running inside Docker on AWS EC2.
