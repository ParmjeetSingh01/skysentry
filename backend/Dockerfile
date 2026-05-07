FROM python:3.11-slim

WORKDIR /app

RUN apt-get update && apt-get install -y libgl1 libglib2.0-0 && rm -rf /var/lib/apt/lists/*

COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# Download YOLOv8 model at build time so it's baked in
RUN python3 -c "from ultralytics import YOLO; m=YOLO('yolov8n.pt'); print('Model downloaded OK')"

COPY . .

CMD ["uvicorn", "main:app", "--host", "0.0.0.0", "--port", "7860"]
