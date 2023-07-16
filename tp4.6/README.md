time docker build . -f Dockerfile.basic
-> construction complete

time docker build . -f Dockerfile.basic
-> construction via cache

time docker build . -f Dockerfile.optim
-> construction complete de la verison optimisée
-> Modification du fichier HELP.md

time docker build . -f Dockerfile.optim
-> Verification que tous les caches sont utilisés
-> Modification d'un fichier java

time docker build . -f Dockerfile.optim
-> Verification que la couche de dépendances est bien utilisée
