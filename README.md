# React Clock

This is a fork of this clock app that includes deployments for Azure Kubernetes Service and Docker.
I have deployed this to my own Azure kubernetes cluster. I have turned off the AKS cluster since mine is a student account. So you can only see the images or clone it and use it for your own deployment.



![AKS Cluster](https://cs210032001def6664e.blob.core.windows.net/pdurgiimages/AKS_cluster.png?sp=r&st=2023-12-03T04:42:49Z&se=2023-12-03T12:42:49Z&spr=https&sv=2022-11-02&sr=b&sig=eQG5KVe5x2ELVjAkDSaAxF0tQLpGGcn5tM%2BjT5rGMsY%3D)



[Add other instructions as needed.]



### App Service Deployment Method:

In Azure cloud shell:

```
git clone https://github.com/jaydestro/react-clock-basic.git

Create ACR
```
az acr create --resource-group $NAME--name $NAMEacr --sku Basic --admin-enabled true

![AKS Registry](https://cs210032001def6664e.blob.core.windows.net/pdurgiimages/container_registry.png?sp=r&st=2023-12-03T05:10:30Z&se=2023-12-03T13:10:30Z&spr=https&sv=2022-11-02&sr=b&sig=vyCPKHgpKtLOsvNoy%2F4BLHZtq0SFU%2BATItI8vIZas%2FU%3D)

az acr build  --registry $NAMEacr --image react-clock-basic:v1 .
```

change the image name in deployment file : image: aksreg018.azurecr.io/react-clock-basic:v1

kubectl apply -f .\deployment.yaml
kubectl apply -f .\loadbalancer.yaml
kubectl get services

![Pick the external ip and paste in browser] (https://cs210032001def6664e.blob.core.windows.net/pdurgiimages/manifests_to_run.png?sp=r&st=2023-12-03T05:14:58Z&se=2023-12-03T13:14:58Z&spr=https&sv=2022-11-02&sr=b&sig=5xV9gQG2cXOoUiUwr9cReO3TOAPxkVRgyaxW40Ebe6o%3D)


![APP running on browser] (https://cs210032001def6664e.blob.core.windows.net/pdurgiimages/App%20on%20browser.png?sp=r&st=2023-12-03T05:16:38Z&se=2023-12-03T13:16:38Z&spr=https&sv=2022-11-02&sr=b&sig=BFQZWCVi3Jy6LY1OgURtvlxIGR4pnKoBXnq2rCwCArk%3D)


## Authors

* **Douglas Minnaar** - *Initial work* - [drminnaar](https://github.com/drminnaar)
** Modified by - Pooja Durgi to deploy to Azure Portal **

