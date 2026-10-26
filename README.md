1. Install argo
---------------

# argo install

helm dependency build ./deploy-argocd

helm install argo-deployment ./deploy-argocd -n argocd --create-namespace

# get admin crews

kubectl get secrets -n argocd argocd-initial-admin-secret -o yaml

echo "eDkxYWxuOHozU3dPVFBaLQ==" | base64 -d

kubectl port-forward -n argocd svc/argo-deployment-argocd-server 8080:80


2. Install project and repository
---------------------------------

helm install argo-project ./deploy-argo-projects/

3. Install apps
---------------

 helm install argo-apps ./deploy-argo-apps/
