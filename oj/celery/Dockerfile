FROM jxxn/dmoj-base:latest

ENTRYPOINT celery -A dmoj_celery worker -l info --concurrency=2

RUN apt update
RUN pip install --upgrade setuptools
