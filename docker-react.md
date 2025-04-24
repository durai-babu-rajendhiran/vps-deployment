# 🚀 React App Deployment with Docker - Step by Step Guide

This guide helps you Dockerize a React app, build and run containers, export/import images as `.tar`, and manage Docker lifecycle commands.

---

## 🏗️ Step 1: Build the React App
```bash
npm run build
```
## 🐳 Step 2: Create Dockerfile in Project Root
```bash
# Step 1: Build React App
FROM node:18 AS build
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build

# Step 2: Serve with NGINX
FROM nginx:alpine
COPY --from=build /app/build /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
```
## 📂 Step 3: Create .dockerignore
```bash
node_modules
build
.dockerignore
Dockerfile
*.md
```

## 🧱 Step 4: Build Docker Image
```bash
docker build -t my-react-app .
```


## 🏃‍♂️ Step 5: Run Docker Container
```bash
docker run -d -p 3000:80 --name react-container my-react-app
```
## 🗃️ Step 6: Export Image as .tar
```bash
docker save -o my-react-app.tar my-react-app
```
## 📥 Step 7: Load Image on Another System
```bash
docker load -i my-react-app.tar
```
## 🚀 Step 8: Run Container from Loaded Image
```bash
docker run -d -p 3000:80 --name react-container my-react-app
```

## 🧹 Step 9: Docker Cleanup & Management Commands

| Command                                       | Description                 |
|----------------------------------------------|-----------------------------|
| `docker ps`                                   | List running containers     |
| `docker ps -a`                                | List all containers         |
| `docker stop react-container`                | Stop the container          |
| `docker rm react-container`                  | Remove the container        |
| `docker images`                               | List all images             |
| `docker rmi my-react-app`                    | Remove image                |
| `docker rmi -f my-react-app`                 | Force remove image          |
| `docker load -i file.tar`                    | Load image from tar         |
| `docker save -o file.tar image-name`         | Save image as tar           |


