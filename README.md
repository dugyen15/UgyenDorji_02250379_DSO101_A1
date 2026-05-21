# UgyenDorji_02250379_DSO101_A1
# DSO101 - Continuous Integration and Continuous Deployment
**Student Name:** Ugyen Dorji  
**Student ID:** 02250379  
**Module:** DSO101 - CI/CD  


## Overview
This assignment demonstrates CI/CD practices by building and deploying a full-stack To-Do List web application using Docker, Docker Hub, Render.com, and GitHub Actions.

**Tech Stack:**
- Frontend: React.js
- Backend: Node.js + Express
- Database: PostgreSQL


## Step 0: Application Setup

### Project Structure
todo-app/
├── backend/
│     ├── Dockerfile
│     ├── .dockerignore
│     ├── db.js
│     ├── server.js
│     └── package.json
├── frontend/
│     ├── Dockerfile
│     ├── .dockerignore
│     ├── src/App.js
│     └── package.json
└── render.yaml

### Environment Variables
Backend `.env`:
DB_HOST=localhost
DB_USER=postgres
DB_PASSWORD=yourpassword
DB_NAME=todoapp
DB_PORT=5432
PORT=5000
Frontend `.env`:
REACT_APP_API_URL=http://localhost:5000

### Local App Screenshot
![alt text](<Screenshot 2026-05-21 003442.png>)



## Part A: Deploying Pre-built Docker Images

### Step 1: Build and Push Docker Images

Backend image build and push:
docker build -t theugyen15/be-todo:02250379 ./backend
docker push theugyen15/be-todo:02250379

Frontend image build and push:
docker build -t theugyen15/fe-todo:02250379 ./frontend
docker push theugyen15/fe-todo:02250379

### Docker Hub Screenshots
![alt text](<Screenshot 2026-05-21 150004.png>) 
![alt text](<Screenshot 2026-05-21 150138.png>)


### Step 2: Deploy on Render.com

**Database:** Created PostgreSQL database `todo-db` on Render.com

**Backend Service:**
- Image: `theugyen15/be-todo:02250379`
- URL: https://be-todo-02250379.onrender.com

**Frontend Service:**
- Image: `theugyen15/fe-todo:02250379`
- URL: https://fe-todo-02250379.onrender.com

### Render Deployment Screenshots
![alt text](<Screenshot 2026-05-21 144902.png>)
![alt text](<Screenshot 2026-05-21 144949.png>)

### Live App Screenshot
![alt text](<Screenshot 2026-05-21 003442.png>)



## Part B: Automated Image Build and Deployment

### Step 1: GitHub Repository
Repository: https://github.com/dugyen15/UgyenDorji_02250379_DSO101_A1

### Step 2: render.yaml Configuration
The `render.yaml` file at the root of the repository configures automated multi-service deployment on Render.com. Every push to the `main` branch triggers a new deployment.

### Step 3: GitHub Actions Workflow
The `.github/workflows/deploy.yml` file automatically triggers Render deployments on every push to `main` using Render Deploy Hooks.

### GitHub Actions Screenshot
![alt text](<Screenshot 2026-05-21 144109.png>)

---

## Live URLs
| Service | URL |
|---------|-----|
| Frontend | https://fe-todo-02250379.onrender.com |
| Backend | https://be-todo-02250379.onrender.com |
| GitHub | https://github.com/dugyen15/UgyenDorji_02250379_DSO101_A1 |