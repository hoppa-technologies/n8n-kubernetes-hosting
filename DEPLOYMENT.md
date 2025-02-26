### TG Notes for deployment

```BASH
az login
az aks get-credentials --resource-group scout-doc-intelligence_group --name hoppa-n8n
kubernetes-hosting>kubectl apply -f https://github.com/cert-manager/cert-manager/releases/latest/download/cert-manager.crds.yaml
kubectl create namespace cert-manager
kubectl apply -f https://github.com/cert-manager/cert-manager/releases/latest/download/cert-manager.yaml --namespace cert-manager
kubectl apply -f .
kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/main/deploy/static/provider/cloud/deploy.yaml
```

Note: I did have to do some stuff with restarting the cert-manager to get cluster-issuer to deploy. 

```BASH
kubectl get svc -n n8n
```

Then copy the external IP into Azure DNZ Zone A recordset.