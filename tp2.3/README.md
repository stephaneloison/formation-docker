docker run -d --rm -p 90:80 nginx
docker run -d --rm -p 91:80 nginx
docker run -d --rm -p 92:80 nginx
curl http://127.0.0.1:90
curl http://127.0.0.1:91
curl http://127.0.0.1:92

