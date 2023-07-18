# Création du projet angularSample sans environnement node/ng en local

docker run -u $(id -u) --rm -v $(pwd):/app trion/ng-cli ng new angularSample

# Création de l'image de run via le docker multistage

docker build . -t tp47

