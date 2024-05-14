Steps for this Practical :
------------------------------------------
------------------------------------------


Let's walk through a practical example of using multi-stage Docker builds with a Python application. In this example, we'll create a simple Flask web application and use a multi-stage Dockerfile to build a lean Docker image for running the application.

### Step 1: Create a Python Flask Application

First, let's create a simple Python Flask application. Create a directory for your project and navigate into it:

```bash
mkdir flask-app
cd flask-app
```

Create a file named `app.py` with the following content:

```python
from flask import Flask

app = Flask(__name__)

@app.route('/')
def hello():
    return "Hello from Flask!"

if __name__ == '__main__':
    app.run(host='0.0.0.0', port=5000)
```

### Step 2: Create a Requirements File

Create a file named `requirements.txt` to specify the Python dependencies for your application:

```plaintext
Flask==2.0.2
```

### Step 3: Create a Multi-Stage Dockerfile

Create a file named `Dockerfile` in the same directory with the following content for the multi-stage Docker build:

```Dockerfile
# Stage 1: Build the application
FROM python:3.9 AS builder
WORKDIR /app
COPY app.py requirements.txt /app/
RUN pip install --no-cache-dir -r requirements.txt

# Stage 2: Create the production image
FROM python:3.9-slim
WORKDIR /app
COPY --from=builder /app /app
CMD ["python", "app.py"]
```

### Step 4: Build the Docker Image

Now, build the Docker image using the multi-stage Dockerfile:

```bash
docker build -t flask-app .
```

### Step 5: Run the Docker Container

Finally, run a Docker container based on the built image:

```bash
docker run -d -p 5000:5000 flask-app
```

### Step 6: Access the Flask Application

Open a web browser or use `curl` to access the Flask application running in the Docker container:

```bash
curl http://localhost:5000
```

You should see the message "Hello from Flask!" displayed in the output.


Thank You.
