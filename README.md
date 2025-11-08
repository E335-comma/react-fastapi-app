### Project Overview
#### This project is about :
- Dockerizing React-FastAPI-App Using Amazon ECR
- Deploying the dockerized app to EC2

---

## Steps:
### Step 1: Creating Dockerfile for React-app and FastAPI
- I created a dockerfile for my API server(Fastapi) and built it with the command:
```bash
docker build -t <image-name> .
```
- I also created a dockerfile for my react-app which is the frontend and built it.

### Step 2: Create a Private and Public Repository for each app in Amazon ECR.
 Here are the steps I followed when pushing my images to the repositories created. 
- Authenticated to my aws using my credentials. I ran the command: 
```bash
aws configure
```
to authenticate.

- Login to AWS ECR using the command:
``bash
aws ecr get-login-password --region <aws_region> | docker login --username AWS --password-stdin <account_id>.dkr.ecr.<aws_region>.amazonaws.com
```
- I built my docker image using the command:
```bash
docker build -t <image_name> .
```
- I tagged my image so that it can be pushed:
```bash
docker tag <image_name> <account_id>.dkr.ecr.<aws_region>.amazonaws.com/<repository_name>
```
- I pushed the image to my newly created repository:
```bash
 docker push <account_id>.dkr.ecr.<aws_region>.amazonaws.com/<repository_name>
 ```

---

### Step 3: Create an EC2 Instance for deploying the app, allowing port 3000 and 8000. And add necessary roles
- I ssh into my instance:

- Update and upgrade:
```bash
sudo apt update -y
sudo apt upgrade
```
- Installed docker and docker-compose:
```bash
sudo apt install docker.io docker-compose
```
- Install awscli:
```bash
```
- Authenticate into AWS:
```bash
aws configure
```
- Login to ECR:
```bash
aws ecr get-login-password --region <aws_region> | docker login --username AWS --password-stdin <account_id>.dkr.ecr.<aws_region>.amazonaws.com
```
- Copy docker-compose file into EC2
- Build:
```bash
docker-compose up --build
```
- Test react-fastapi-app using the EC2 instance public Ip.

You can check my result using the ec2 public ip below:





    