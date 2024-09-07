FROM jxxn/dmoj-base:latest

EXPOSE 8000

ENTRYPOINT uwsgi --ini uwsgi.ini

RUN apt update
RUN pip install --upgrade setuptools
