docker run --rm -d -v $(pwd):/usr/src/app -w /usr/src/app -p 3000:3000 --name nodeapp node:18 npm start
curl http://127.0.0.1:3000

docker run --rm busybox wget http://nodeapp:3000

docker run --rm --network=host busybox wget http://127.0.0.1:3000

docker run --rm --network=host -p 666:666 busybox wget http://127.0.0.1:3000

docker network create test-network
docker network ls

docker run --rm -d -v $(pwd):/usr/src/app -w /usr/src/app -p 3000:3000 --network=test-network --name nodeapp node:18 npm start
docker ps
docker run --rm --network=test-network -p 666:666 busybox wget http://nodeapp:3000
