<img width="50%" src="https://raw.githubusercontent.com/kubero-dev/kubero/main/docs/logo/kubero-logo-horizontal.png">

<br>
<br>
Kubero brings the convinience of Heroku/platform.sh to your kubernetes cluster. Your developers should not need to worry about the underlying infrastructure and deployment.
<br>
Pleas visit the main repository for docs and more information 
https://github.com/kubero-dev 
<br>


## Installation of operator controller without operator hub via kustomize and a single instance of kubero via helm (not published yet)
Note: Add any extra configuration variables to the kubero-secrets secret.
```bash
git clone https://github.com/kubero-dev/kubero-operator.git
cd kubero-operator
# kubectl apply operator controller
kubectl apply --kustomize  config/default 
# Add kubero-ui instance
helm install kubero ./helm-charts/kubero -n kubero --create-namespace --values custom_values.yaml
kubectl create secret generic kubero-secrets -n kubero --from-literal=KUBERO_WEBHOOK_SECRET=$(openssl rand -hex 20) --from-literal=KUBERO_SESSION_KEY=$(openssl rand -hex 20)
```
