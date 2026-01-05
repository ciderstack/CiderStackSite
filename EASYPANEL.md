# Easypanel Deployment Guide

## Quick Start

### Step 1: Connect Repository
1. Go to your Easypanel dashboard
2. Click "New App" or "Add Service"
3. Select "GitHub" or "Git Repository"
4. Connect your repository: `ciderstack/CiderStackSite`

### Step 2: Configure Build Settings

**Recommended: Dockerfile Method**

1. **Build Method**: Select "Dockerfile"
2. **Dockerfile Path**: `Dockerfile` (default, already in root)
3. **Port**: `8080`
4. **Start Command**: Leave empty (Dockerfile CMD handles this)

**Alternative: Buildpacks Method**

1. **Build Method**: Select "Buildpacks"
2. **Start Command**: 
   ```bash
   gunicorn -w 4 -b 0.0.0.0:8080 app:app
   ```
3. **Port**: `8080`

### Step 3: Deploy

Click "Deploy" and Easypanel will:
- Build your application
- Start the container/service
- Provide you with a URL

## What Gets Deployed

- Flask application (`app.py`)
- All templates and static files
- Gunicorn as the production server
- Runs on port 8080

## Notes

- The Dockerfile uses gunicorn with 4 workers
- No environment variables required
- All dependencies are installed from `requirements.txt`
- Images are served from the `/images` path

