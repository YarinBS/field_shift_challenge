FROM python:3.12-slim

ENV PYTHONDONTWRITEBYTECODE=1 \
    PYTHONUNBUFFERED=1 \
    PYTHONPATH=/workspace/model/src:/workspace/app/backend/src

WORKDIR /workspace
COPY app/backend/requirements.txt /workspace/app/backend/requirements.txt
RUN pip install --no-cache-dir -r /workspace/app/backend/requirements.txt

COPY model/src /workspace/model/src
COPY app/backend/src /workspace/app/backend/src

EXPOSE 8000
CMD ["uvicorn", "main:app", "--app-dir", "/workspace/app/backend/src", "--host", "0.0.0.0", "--port", "8000"]
