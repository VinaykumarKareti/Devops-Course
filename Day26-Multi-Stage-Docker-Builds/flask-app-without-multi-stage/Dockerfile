FROM python:3.9
WORKDIR /app
COPY app.py requirements.txt /app/
RUN pip install --no-cache-dir -r requirements.txt

CMD ["python3","app.py"]

