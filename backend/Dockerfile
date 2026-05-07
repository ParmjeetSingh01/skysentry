FROM python:3.11-slim
WORKDIR /app
RUN apt-get update && apt-get install -y libgl1 libglib2.0-0 wget && rm -rf /var/lib/apt/lists/*
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt
RUN wget -q https://github.com/ultralytics/assets/releases/download/v0.0.0/yolov8n.pt -O /app/yolov8n.pt && echo "yolov8n.pt ready"
COPY main.py .
CMD uvicorn main:app --host 0.0.0.0 --port ${PORT:-8000}
