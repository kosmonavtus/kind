## ingress fix secret

kubectl create secret generic ingress-nginx-admission-token \
  --namespace ingress-nginx \
  --from-literal=token=$(openssl rand -hex 32)

## argocd default password extract

k get secrets -n argocd argocd-initial-admin-secret  -o yaml | yq eval '.data.password'  | base64 -d