# Jenkins CI/CD assignment application

Independent, repository-ready Flask and Express copies of AWS Task 3 for later separate Jenkins pipelines. Jenkins installation, GitHub integration, and deployment are intentionally out of scope.

`Backend/` is a Flask API on port 5000. `Frontend/` is an Express/EJS server on port 3000. Backend validation uses `python -m py_compile Backend/app.py`; frontend validation uses `node --check Frontend/server.js` and `cd Frontend; npm ci`.

Run locally with `pip install -r Backend/requirements.txt; python Backend/app.py` and, in a separate terminal, `cd Frontend; npm ci; $env:BACKEND_URL='http://127.0.0.1:5000'; npm start`.

Compose validation uses `docker compose build`, `docker compose up -d`, `docker compose ps`, and `Invoke-WebRequest http://127.0.0.1:3000/api/health -UseBasicParsing`; stop with `docker compose down`. Compose injects `BACKEND_URL=http://backend:5000`, and CI can build each Dockerfile independently.
