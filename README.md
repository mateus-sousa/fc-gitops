kind create cluster --name=gitopsfc

curl -s "https://raw.githubusercontent.com/kubernetes-sigs/kustomize/master/hack/install_kustomize.sh"  | bash

./kustomize edit set image goserver=mateuspanda/gitopsfc:novatag