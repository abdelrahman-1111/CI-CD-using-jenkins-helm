FROM python:3.9-alpine

RUN apk add --update redis
WORKDIR /app
COPY DevOps-Challenge/requirements.txt requirements.txt
RUN pip3 install -r requirements.txt
ENV ENVIRONMENT=PROD
ENV HOST=localhost
ENV REDIS_PORT=6379
ENV REDIS_HOST=localhost
ENV PORT=8000
EXPOSE 8000
ENV REDIS_DB=0
COPY ./DevOps-Challenge/ .
CMD ["sh","run.sh"]
