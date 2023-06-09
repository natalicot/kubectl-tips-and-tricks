kind create cluster --name sdp --config ./cluster/sdp.yaml

kubectl apply -f ./resources/ns.yaml

kubectl apply -f ./resources/demo-deployment.yaml

kubectl apply -f ./resources/service.yaml

kubectl config set-context --current --namespace=sdp
