# IDProj infrastructure

This repository contains the infrastructure code for the IDProj project.
This infrastructure runs on DigitalOcean.


## Journal

### NGINX ingress controller
* Instalare ingress-nginx cu helm
  `helm install nginx-ingress ingress-nginx/ingress-nginx --set controller.publishService.enabled=true`
* Obtinem Load balancer automat in Digitalocean

### Cluster issues
* Instalam cert-manager cu helm
  `helm install cert-manager jetstack/cert-manager --namespace cert-manager --version v1.11.1 --set installCRDs=true`
* Adaugam cluster issuer pentru cert-manager
  `production-issuer.yaml`

### Configure example apps to test cert-manager and ingress
* Vezi folder-ul `example`

### Argocd
* Instalare argocd cu helm
  `helm install argocd argo/argo-cd --namespace argocd --version 5.32.1`
* Add A record for argocd.idproj.me
* Configurare ingress pt argocd `argocd-ingress.yaml`
```
Check it here: argocd.idproj.me
user: admin
pass: 3uJg8njn6O5ByxVn
```

### Portainer
* Instalare portainer cu helm
  `helm install portainer portainer/portainer --version 1.0.42 -n portainer --set service.type=ClusterIP`
* Configurare ingress pt portainer `portainer-ingress.yaml`
```
Check it here: portainer.idproj.me
user: admin
pass: cty5rmv9YTU-wjx4vum
```