docker run --rm -d -p 90:80 nginx
docker cp index.html CONTAINER_ID:/usr/share/nginx/html/.
curl http://127.0.0.1:90
docker ps
docker stop XXXX


docker cp CONTAINER_ID:/etc/nginx/nginx.conf .
ls
docker ps
docker stop XXXX


