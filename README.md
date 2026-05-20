# AI Video Platform

[![Deploy to Render](https://render.com/images/deploy-to-render-button.svg)](https://render.com/deploy?repo=https://github.com/YOUR_USERNAME/ai-video-platform)

A production-ready AI video generation platform. Generate videos from text and images using state-of-the-art AI models.

## 🚀 Deploy from Phone (No Computer Needed)

### Step 1: Fork to GitHub
1. Download the ZIP from this repository
2. Go to [github.com](https://github.com) on your phone browser
3. Create a new repository (click + → New repository)
4. Name it `ai-video-platform`
5. Upload all files from the ZIP (Add file → Upload files)

### Step 2: Deploy to Render
1. Go to [render.com](https://render.com) and sign up (free)
2. Click **"New +"** → **"Blueprint"**
3. Connect your GitHub account
4. Select the `ai-video-platform` repo
5. Click **"Apply"** — Render reads `render.yaml` and creates all services automatically

### Step 3: Add Secrets
After deploy, go to each service in Render Dashboard → Environment:

| Service | Required Secrets |
|---------|-----------------|
| **backend-api** | `REPLICATE_API_TOKEN` or `RUNWAY_API_KEY` |
| **backend-api** | `AWS_ACCESS_KEY_ID`, `AWS_SECRET_ACCESS_KEY`, `S3_BUCKET`, `S3_ENDPOINT` |
| **celery-worker** | Same AI + S3 keys as backend |
| **frontend** | `NEXTAUTH_SECRET` (auto-generated), `GOOGLE_CLIENT_ID` (optional) |

Get a free Replicate token: [replicate.com/account/api-tokens](https://replicate.com/account/api-tokens)

### Step 4: Done
- Frontend: `https://ai-video-frontend.onrender.com`
- API: `https://backend-api-xxxxx.onrender.com`

## 🏗️ Architecture

- **Frontend**: Next.js 14 + Tailwind + Framer Motion
- **Backend**: FastAPI + Async SQLAlchemy + PostgreSQL
- **Worker**: Celery + Redis for background generation
- **Storage**: S3-compatible (AWS, R2, MinIO)
- **AI**: Replicate, Runway, or custom providers

## 📁 Project Structure

```
├── backend/          # FastAPI API server
├── frontend/         # Next.js web app
├── worker/           # Celery background workers
├── render.yaml       # Render.com blueprint
├── railway.json      # Railway.app config
├── docker-compose.yml # Local development
└── setup.sh          # Local setup script
```

## 🔧 Local Development (on Computer)

```bash
# 1. Clone your GitHub repo
git clone https://github.com/YOUR_USERNAME/ai-video-platform.git
cd ai-video-platform

# 2. Run interactive setup
chmod +x setup.sh
./setup.sh

# 3. Access
# Frontend: http://localhost:3000
# API:      http://localhost:8000
```

## 💳 Credit System

- New accounts get **50 free credits**
- Each generation costs **10 credits**
- Add Stripe keys to sell credit packs

## 🔌 Adding Custom GPU Provider

See `backend/app/services/ai_providers/` — implement `BaseVideoProvider` and register in `PROVIDERS` dict for unlimited generation on your own hardware.

## License

MIT
