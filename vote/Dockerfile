# vote/Dockerfile
FROM python:3.12-alpine AS builder

WORKDIR /app

# Copy requirements first for better caching
COPY requirements.txt .

# Install dependencies in builder stage
RUN pip install --user --no-cache-dir -r requirements.txt

# Copy app code
COPY . .

# Final runtime image
FROM python:3.12-alpine
WORKDIR /app

# Copy only installed packages from builder
COPY --from=builder /root/.local /root/.local
# Copy app code
COPY --from=builder /app .

ENV PATH=/root/.local/bin:$PATH
EXPOSE 80

CMD ["python", "app.py"]
