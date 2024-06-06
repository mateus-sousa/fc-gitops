kind create cluster --name=gitopsfc

curl -s "https://raw.githubusercontent.com/kubernetes-sigs/kustomize/master/hack/install_kustomize.sh"  | bash

./kustomize edit set image goserver=mateuspanda/gitopsfc:novatag


instalar argocd localment:

kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml

kubectl port-forward svc/argocd-server -n argocd 8080:443

receber senha padrao do argo via kubectl:
kubectl get secret argocd-initial-admin-secret -n argocd -o jsonpath="{.data.password}" | base64 -d; echo

argocd login localhost:8080
usuario: admin
usar senha que o comando anterior forneceu

kubectl config current-context


COnsulta: https://github.com/badtuxx/DescomplicandoArgoCD