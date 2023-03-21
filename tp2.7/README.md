docker run --rm -v $(pwd):/usr/src/app -w /usr/src/app node:18 npm install

docker run --rm -d -v $(pwd):/usr/src/app -w /usr/src/app -p 3000:3000 node:18 npm start
curl http://127.0.0.1:3000

docker ps
docker stop XXXX
