# Création du projet angularSample sans environnement node/ng en local

docker run -u $(id -u) --rm -v $(pwd):/app trion/ng-cli ng new angularSample

# Création de l'image de run via le docker multistage

docker build ./angularSample -f ./Dockerfile -t tp46

docker run --rm -p 80:80 tp46