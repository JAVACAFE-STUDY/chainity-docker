FROM node:8

MAINTAINER chihwan "clghks@gmail.com"

# 라이브러리 업데이트
RUN apt-get update

WORKDIR /usr/src/app

# git 설치
RUN apt-get install -y git

RUN apt-get install build-essential
RUN npm install -g pm2

# Community-rewards 코드 받기
RUN git clone https://github.com/JAVACAFE-STUDY/community-rewards.git
WORKDIR /usr/src/app/community-rewards

WORKDIR /usr/src/app/community-rewards/backend

# 설정 파일 복사
COPY .env .env

EXPOSE 3000
CMD [ "npm", "run", "deploy" ]