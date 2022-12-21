docker-compose up –d
docker-compose down

docker exec demo_traefik ping demo_app1

docker exec demo_traefik ping demo_app2

docker exec demo_app1 bash -c "apt-get update; apt-get install -y iputils-ping; ping demo_app2“

docker exec demo_app1 ls /usr/src/app/shared

docker exec demo_app2 ls /usr/src/app/shared

docker exec demo_app2 bash -c "echo 'sharedContent' > /usr/src/app/shared/sharedFile“

docker exec demo_app2 ls /usr/src/app/shared

docker exec demo_app1 more /usr/src/app/shared/sharedFile
