FROM node:22

RUN npm install -g npm@6

RUN npm cache clean --force

RUN npm install

RUN npm install mathoid && \
    ln -sfv /node_modules/mathoid/app.js /node_modules/app.js

EXPOSE 10044
WORKDIR /node_modules/mathoid
CMD /node_modules/mathoid/server.js

RUN npm install
