docker build . -f ./DokerfileFat
docker inspect XXXXX | grep Size

docker build . -f ./DokerfileSlim
docker inspect XXXXX | grep Size