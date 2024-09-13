FROM python:3.12-slim-bookworm

RUN apt-get update && \
    apt-get install -y --no-install-recommends \
        curl gnupg git unzip xvfb libxi6 libgconf-2-4 exiftool fontconfig fonts-noto-cjk fonts-liberation && \
    curl -sS -o - https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add && \
    echo "deb [arch=amd64] https://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google-chrome.list && \
    sed -i 's/^Components: main$/& contrib non-free/' /etc/apt/sources.list.d/debian.sources && \
    apt-get update && \
    apt-get install -y --no-install-recommends google-chrome-stable && \
    rm -rf /var/lib/apt/lists/* && \
    wget https://storage.googleapis.com/chrome-for-testing-public/128.0.6534.0/linux64/chromedriver-linux64.zip && \
    unzip chromedriver-linux64.zip && \
    mv ./chromedriver-linux64/chromedriver /usr/bin/chromedriver && \
    chmod +x /usr/bin/chromedriver && \
    rm chromedriver-linux64.zip && \
    useradd -m pdfoid

RUN fc-cache -fv

RUN git clone https://github.com/DMOJ/pdfoid.git pdfoid
WORKDIR /pdfoid/
RUN pip3 install -e .

RUN rm /pdfoid/pdfoid/backends/direct.py
RUN wget -P /pdfoid/pdfoid/backends/ https://github.com/jxxxxxxn/oj_docker/raw/main/direct.py

ENV CHROMEDRIVER_PATH=/usr/bin/chromedriver
ENV EXIFTOOL_PATH=/usr/bin/exiftool
ENV CHROME_PATH=/usr/bin/google-chrome-stable

EXPOSE 8888
USER pdfoid
ENTRYPOINT pdfoid --address=pdfoid --port=8888

