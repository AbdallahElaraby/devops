# vote/Dockerfile
FROM python:3.12-alpine AS builder
WORKDIR /app
COPY requirements.txt .
RUN pip install --user --no-cache-dir -r requirements.txt
COPY . .
FROM python:3.12-alpine
WORKDIR /app
RUN adduser -D appuser
COPY --from=builder /root/.local /usr/local
COPY --from=builder /app .
USER appuser
EXPOSE 80
CMD ["python", "app.py"]
