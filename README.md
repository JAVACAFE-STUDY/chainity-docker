# 몽고 디비 실행 
```
docker run --name mongo -d -p 27017:27017 -v /data:/data/db mongo --noauth --bind_ip=0.0.0.0
```

# Geth 실행 
```
docker run -d --name ethereum-node -v /Users/alice/ethereum:/root -p 8545:8545 ethereum/client-go --rpc --rinkeby --rpcaddr "0.0.0.0"
```

# API 서버 빌드 및 실행 
```
// profile 파일 경로
cd /
sudo mkdir /data
cd data
sudo mkdir profile
sudo chmod -Rf 777 profile

docker build -t community-rewards/backend .
docker run -d -p 3000:3000 -v /data/profile:/data/profile community-rewards/backend
```

# API 서버 설정 파일 변경 
```
docker cp .env_dev [container id]:/usr/src/app/community-rewards/backend/.env
sudo docker stop [container id]
sudo docker start [container id]

// 예제 
[container id] = 9c1832636416
docker cp .env_dev 9c1832636416:/usr/src/app/community-rewards/backend/.env
sudo docker stop 9c1832636416
sudo docker start 9c1832636416
```


# Admin 서버 빌드 및 실행 
```
docker build -t community-rewards/admin .
docker run -d -p 8080:80 community-rewards/admin
```

# Web 서버 빌드 및 실행 
```
docker build -t community-rewards/web .
docker run -d -p 9000:80 community-rewards/web
```