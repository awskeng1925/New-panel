FROM python:3.11-slim

RUN apt-get update && apt-get install -y \
    curl \
    && pip install playwright \
    && playwright install chromium \
    && playwright install-deps

WORKDIR /app
COPY requirements.txt .
RUN pip install -r requirements.txt

COPY . .
CMD ["python", "app.py"]
