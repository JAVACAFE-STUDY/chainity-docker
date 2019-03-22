FROM node:8

MAINTAINER chihwan "clghks@gmail.com"

# 라이브러리 업데이트
RUN apt-get update

RUN npm install webpack
RUN npm i -D webpack-cli
RUN npm install --save-dev webpack-dev-server 
RUN npm install --save-dev webpack-dev-middleware webpack-hot-middleware

# git 설치
RUN apt-get install -y git

WORKDIR /usr/src/app

RUN git clone https://github.com/clghks/community-rewards.git
WORKDIR /usr/src/app/community-rewards

RUN npm install
RUN npm install --prefix backend/
RUN npm install --prefix frontend/

COPY .env backend/.env

EXPOSE 8080
CMD [ "npm", "start" ]
