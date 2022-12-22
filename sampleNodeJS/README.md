# Dev

docker run --rm -v $(pwd):/usr/src/app -w /usr/src/app node:18 npm install
docker run --rm -d -v $(pwd):/usr/src/app -w /usr/src/app -p 3000:3000 node:18 npm start
curl http://127.0.0.1:3000

# Create Image

docker build --tag testslo.azurecr.io/samplenodejs .
docker run --rm -p 3000:3000 testslo.azurecr.io/samplenodejs

# Login & push

az login
az acr login --name testslo
docker push testslo.azurecr.io/samplenodejs

# Add containerapp (https://learn.microsoft.com/en-us/azure/container-apps/get-started?tabs=bash)

az extension add --name containerapp --upgrade

az provider register --namespace Microsoft.App
az provider register --namespace Microsoft.OperationalInsights

# Choix de la souscription

az account subscription list
az account subscription enable 892f5f5a-af92-4453-88b4-424a03cded2f

# Create Resource Group

az account list-locations
az group create --name sloResourceGroup --location francecentral

RESOURCE_GROUP="niji-sb-stephane-loison"
LOCATION="westeurope"
CONTAINERAPPS_ENVIRONMENT="slo-environment"

# Create enviornment

az containerapp env create \
  --name $CONTAINERAPPS_ENVIRONMENT \
  --resource-group $RESOURCE_GROUP \
  --location $LOCATION

az containerapp env delete \
  --name $CONTAINERAPPS_ENVIRONMENT \
  --resource-group $RESOURCE_GROUP

# Create a user-assigned identity

az identity create \
 --resource-group $RESOURCE_GROUP \
 --name slo-container-app-identity \
 --output json

# assigne t

# Create container app

az containerapp create \
  --name slo-container-app \
  --resource-group $RESOURCE_GROUP \
  --environment $CONTAINERAPPS_ENVIRONMENT \
  --image testslo.azurecr.io/samplenodejs \
  --registry-identity /subscriptions/892f5f5a-af92-4453-88b4-424a03cded2f/resourcegroups/niji-sb-stephane-loison/providers/Microsoft.ManagedIdentity/userAssignedIdentities/slo-container-app-identity \
  --registry-server testslo.azurecr.io \
  --min-replicas 0 \
  --max-replicas 1 \
  --target-port 3000 \
  --ingress 'external' \
  --query properties.configuration.ingress.fqdn

az containerapp delete \
  --name slo-container-app \
  --resource-group $RESOURCE_GROUP