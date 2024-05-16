#Stage 1: Build the Application
FROM python:3.9 AS builder
WORKDIR /app
COPY app.py requirements.txt /app/
RUN pip install --no-cache-dir -r requirements.txt

# Stage 2: Create teh production image
FROM python:3.9-slim
WORKDIR /app
COPY --from=builder /app /app
CMD ["python3","app.py"]

