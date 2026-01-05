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

## Project Structure

- `app.py` - Flask application
- `templates/` - HTML templates
- `images/` - Screenshot images
- `venv/` - Virtual environment (not tracked in git)

