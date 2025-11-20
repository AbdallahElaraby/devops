FROM python:3.12-alpine

WORKDIR /seed

RUN apk add --no-cache bash apache2-utils

COPY make-data.py generate-votes.sh ./

RUN python3 make-data.py && \
    chmod +x generate-votes.sh
CMD ["sh", "-c", "./generate-votes.sh"]