docker build . -t tp4.3
docker run --rm -p 80:80 tp4.3
curl http://127.0.0.1
