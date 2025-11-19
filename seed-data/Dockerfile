# seed-data/Dockerfile
FROM python:3.12-slim AS builder
WORKDIR /seed
COPY ./ ./
RUN chmod +x generate-votes.sh
RUN python3 make-data.py

FROM python:3.12-alpine
WORKDIR /seed
COPY --from=builder /seed .
RUN apk add --no-cache bash apache2-utils curl
CMD ["./generate-votes.sh"]

