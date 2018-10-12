FROM python:3.4.9-alpine
# RUN apt-get update && apt-get -y install netcat && apt-get clean
WORKDIR /app

COPY requirements.txt ./
RUN apk update && apk add --no-cache --virtual .build-deps \
    gcc \
    musl-dev \
    && pip install --no-cache-dir -r requirements.txt \
    && apk del .build-deps

COPY config.yml ./
COPY run.sh ./
COPY gateway.py ./

RUN chmod +x ./run.sh

CMD ["sh", "run.sh"]
