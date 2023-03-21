docker run --rm -d -p 90:80 -v $(pwd)/index.html:/usr/share/nginx/html/index.html nginx
curl http://127.0.0.1:90

echo ‘well done sir !’ > index.html
curl http://127.0.0.1:90

docker ps
docker stop XXXXX

docker run --rm -d -p 90:80 -v index.html:/usr/share/nginx/html/index.html nginx
curl http://127.0.0.1:90

docker ps
docker stop XXXXX
