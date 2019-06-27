FROM node:8 as build-stage

MAINTAINER chihwan "clghks@gmail.com"

# 라이브러리 업데이트
RUN apt-get update

WORKDIR /usr/src/app

# git 설치
RUN apt-get install -y git

# 코드 받기
RUN git clone https://github.com/JAVACAFE-STUDY/chainity-landing.git
WORKDIR /usr/src/app/chainity-landing

RUN git remote update
RUN git checkout -t origin/develop

RUN npm install
RUN npm run build

# production stage
FROM nginx:1.14.2 as production-stage
COPY --from=build-stage /usr/src/app/chainity-landing/build /usr/share/nginx/html
COPY default.conf /etc/nginx/conf.d/default.conf
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]