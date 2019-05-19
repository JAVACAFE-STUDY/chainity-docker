# 몽고 디비 실행 
```zsh
docker run --name mongo -d -p 27017:27017 -v /data/community-rewards:/data/db mongo --noauth --bind_ip=0.0.0.0
```

# Geth 실행 
```zsh
docker run -d --name ethereum-node -v /Users/alice/ethereum:/root -p 8545:8545 ethereum/client-go --rpc --rinkeby --rpcaddr "0.0.0.0"
```

# API 서버 빌드 및 실행 
```zsh
// profile 파일 경로
cd /
sudo mkdir /data
cd data
sudo mkdir profile
sudo chmod -Rf 777 profile

docker build -t community-rewards/backend:0.4.0 .
docker run -d -p 3000:3000 -v /data/profile:/data/profile community-rewards/backend:0.4.0
```

# API 서버 설정 파일 변경 
```zsh
docker cp .env_dev [container id]:/usr/src/app/community-rewards/backend/.env
sudo docker stop [container id]
sudo docker start [container id]

// 예제 
[container id] = 9c1832636416
sudo docker cp .env 9c1832636416:/usr/src/app/community-rewards/backend/.env
sudo docker stop 9c1832636416
sudo docker start 9c1832636416
```

# Docker Hub 사용
```zsh
// 업로드
docker tag community-rewards/backend:0.4.0 clghks/community-rewards-backend
docker push clghks/community-rewards-backend:0.4.0

// 실행
docker run -d -p 3000:3000 -v /data/profile:/data/profile clghks/community-rewards-backend:0.4.0
```

# Admin 서버 빌드 및 실행 
### 실행 명령어
```zsh
# 프로젝트 루트 하위 경로 이동
cd APIServer

# .env 환경 설정 파일 수정(slack 통해 공유)
vi .env

# docker image 생성
docker build -t community-rewards/admin:0.3.0 .

# docker container 실행
docker run -d -p 8080:80 community-rewards/admin:0.3.0
```

### TODO
- 소스 코드 변경 반영 (현재 이미지 생성 시점에 받은 소스코드를 받음)

# Web 서버 빌드 및 실행 
```zsh
docker build -t community-rewards/web:0.3.0 .
docker run -d -p 9000:80 community-rewards/web:0.3.0
```