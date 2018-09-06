
# sample-spring-kubernetes-azure

## Login usando o azure cli
```
az login
```

## Criando o grupo de recursos
```
az group create --name spring-sample-aks-resourcegroup --location eastus
```

## Criando o cluster de kubernetes
```
az aks create --resource-group=spring-sample-aks-resourcegroup --name=spring-sample-aks-k8cluster --dns-name-prefix=spring-sample-aks-dns --generate-ssh-keys --node-count 1 --location eastus
```

## Construindo a imagem docker
```
mvn dockerfile:build
```

## Enviando a imagem docker para o registry
```
mvn dockerfile:push
```

## Gerando os recursos com o fabric8
```
mvn fabric8:resource
```

## Aplicando os recursos no kubernetes
```
mvn fabric8:apply
```

## Consultando o deployment
```
kubectl get deployments
```

## Consultando os pods
```
kubectl get pods
```

## Consultando o service (IP Externo)
```
kubectl get svc
```