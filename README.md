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
docker build -t community-rewards/backend .
docker run -d -p 3000:3000 community-rewards/backend
```

# Admin 서버 빌드 및 실행 
```
docker build -t community-rewards/frontend .
docker run -d -p 8080:8080 community-rewards/frontend
```