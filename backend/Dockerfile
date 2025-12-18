# Railway backend service (FastAPI)
# NOTE: TensorFlow 2.13 wheels are compatible with Python 3.10 on Linux.
FROM python:3.10-slim

ENV PYTHONDONTWRITEBYTECODE=1 \
    PYTHONUNBUFFERED=1

WORKDIR /app/backend

# Install Python deps first for better layer caching
COPY requirements.prod.txt ./requirements.prod.txt
RUN pip install --no-cache-dir -r requirements.prod.txt

# Copy application code
COPY . .

# Railway sets PORT; default to 8000 for local Docker runs
ENV PORT=8000 \
    PYTHONPATH=/app/backend

EXPOSE 8000

CMD ["sh", "-c", "uvicorn app.main:app --host 0.0.0.0 --port ${PORT}"]
