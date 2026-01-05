# CiderStack Website

Website for CiderStack - macOS VMs That Clean Up After Themselves.

## Setup

1. Create a virtual environment:
```bash
python3 -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

2. Install dependencies:
```bash
pip install -r requirements.txt
```

3. Run the application:

**Development mode (Flask built-in server):**
```bash
python app.py
```
The site will be available at `http://localhost:8080`

**Production mode (Gunicorn):**

Simple command:
```bash
gunicorn -w 4 -b 0.0.0.0:8080 app:app
```

Command-line options explained:
- `-w 4`: Use 4 worker processes
- `-b 0.0.0.0:8080`: Bind to all interfaces on port 8080
- `--timeout 120`: Set worker timeout to 120 seconds
- `--access-logfile -`: Log access to stdout
- `--error-logfile -`: Log errors to stdout
- `app:app`: Module name (`app.py`) and Flask instance (`app`)

## Deployment on Easypanel

### Option 1: Dockerfile (Recommended)

1. **Connect your GitHub repository** to Easypanel
2. **Create a new app** in Easypanel
3. **Select "Dockerfile"** as the build method
4. **Configure the service:**
   - **Port**: `8080`
   - **Start Command**: (Leave empty, Dockerfile CMD will be used)
   - **Build Command**: (Leave empty, Dockerfile will handle it)

5. **Deploy** - Easypanel will automatically:
   - Build the Docker image using the Dockerfile
   - Run the container with gunicorn on port 8080
   - Set up networking and routing

### Option 2: Buildpacks (Alternative)

1. **Connect your GitHub repository** to Easypanel
2. **Create a new app** in Easypanel
3. **Select "Buildpacks"** as the build method
4. **Configure:**
   - **Start Command**: `gunicorn -w 4 -b 0.0.0.0:$PORT app:app`
   - **Port**: Set to `8080` or use `$PORT` environment variable
5. **Deploy**

### Environment Variables

No environment variables are required for basic deployment. The app will run on port 8080 by default.

## Project Structure

- `app.py` - Flask application
- `templates/` - HTML templates
- `images/` - Screenshot images
- `Dockerfile` - Docker configuration for deployment
- `venv/` - Virtual environment (not tracked in git)

