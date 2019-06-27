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

docker build -t chainity/chainity-api:0.6.0 .
docker run -d -p 3000:3000 -v /data/profile:/data/profile chainity/chainity-api:0.6.0
```

# Web 서버 빌드 및 실행 
```zsh
docker build -t chainity/chainity-web:0.6.0 .
docker run -d -p 9000:80 chainity/chainity-web:0.6.0
```

# Landing 빌드 및 실행 
```zsh
docker build -t chainity/chainity-landing:0.6.0 .
docker run -d -p 9090:80 chainity/chainity-landing:0.6.0
```

# Docker Hub 사용
```zsh
// 업로드
docker tag chainity/chainity-api:0.6.0 chainity/chainity-api:0.6.0
docker push chainity/chainity-api:0.6.0

// 실행
docker run -d -p 3000:3000 -v /data/profile:/data/profile chainity/chainity-api:0.6.0
```