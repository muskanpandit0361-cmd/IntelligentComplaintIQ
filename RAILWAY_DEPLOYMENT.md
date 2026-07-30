# 🚀 Deploying IntelligentComplaintIQ on Railway

This guide walks you through deploying **IntelligentComplaintIQ** to [Railway](https://railway.app).

---

## 📋 Prerequisites
1. A **Railway** account at [railway.app](https://railway.app).
2. A **GitHub** repository containing this project codebase.

---

## ⚡ Deployment Steps

### Option A: One-Click GitHub Deployment (Recommended)

1. **Push your code to GitHub**:
   Ensure all files (including `Procfile`, `railway.json`, `nixpacks.toml`, `Dockerfile`, and `requirements.txt`) are committed and pushed to your GitHub repository.

2. **Log into Railway**:
   Go to [railway.app](https://railway.app) and click **Login** -> **Continue with GitHub**.

3. **Create a New Project**:
   - Click **+ New Project**.
   - Select **Deploy from GitHub repo**.
   - Choose your repository (`IntelligentComplaintIQ-main` or your custom repo name).

4. **Deploy**:
   - Railway will automatically detect the application configuration via `railway.json` / `Procfile` / `nixpacks.toml`.
   - Click **Deploy Now**.
   - Railway will build the environment and start the uvicorn server.

5. **Generate Public URL**:
   - In your Railway project dashboard, click on your service.
   - Go to the **Settings** tab.
   - Scroll to **Networking** -> **Public Networking**.
   - Click **Generate Domain**.
   - Your application will now be live at `https://<your-app-name>.up.railway.app`!

---

### Option B: Railway CLI Deployment

If you prefer using the command line:

1. **Install Railway CLI**:
   ```bash
   npm i -g @railway/cli
   ```
2. **Login**:
   ```bash
   railway login
   ```
3. **Initialize & Link Project**:
   ```bash
   railway init
   ```
4. **Deploy**:
   ```bash
   railway up
   ```
5. **Open Deployed App**:
   ```bash
   railway open
   ```

---

## ⚙️ How It Works on Railway
- **Automatic Port Binding**: Railway dynamically sets the `PORT` environment variable. The app automatically binds to `0.0.0.0:$PORT`.
- **Automatic Seed Data**: If the database starts empty, the backend automatically initializes 2,500 synthetic complaints and executes the 10 AI/ML modules on boot.
- **Frontend & Backend Unified**: The FastAPI backend serves the dashboard interface directly at `/`, while providing all API endpoints under `/api/*`.

---

## 🛡️ Troubleshooting
- **Build Timeout / Failures**: Ensure Railway is using Python 3.10+ (configured automatically via Nixpacks/Dockerfile).
- **Domain 404**: Make sure you generated a public domain under **Settings -> Networking -> Generate Domain**.
