FROM jxxn/dmoj-base:latest

EXPOSE 9999
EXPOSE 9998

ENTRYPOINT python3 manage.py runbridged

RUN apt update
RUN pip install --upgrade setuptools
