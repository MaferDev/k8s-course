minikube status
minikube start

## Validar que el kubectl funcione:

kubectl get pods / kubectl get po
kubectl get pods -l app=front
kubectl get pods -l app=front -o wide (Permite ver mas información)

kubectl port-forward nginx 3000:80

## Crear un pod:

kubectl run NAME --image=nginx:alpine --port=90

kubectl port-forward nginx 7000:90

## Ver los logs del pod

kubectl describe pod NAME

## Eliminar un pod

kubectl delete pod NAME

## Obtener el manifiesto del POD Yaml

kubectl get pod NAME -o yaml

## Ingresar al contenedor dentro de un pod

kubectl exec -ti podtest -- sh

## Ver los logs del pod y seguir en tiempo real

kubectl logs podtest -f

## Crear desde un template yaml

kubectl apply -f pod.yaml
kubectl delete -f pod.yaml

## Ver todos los recursos de Kubectl

kubectl api-resources

## listado de deployments

kubectl get deployment --show-labels

## Definir la causa del deployment

kubectl apply -f dep.yaml --record

## Hacer un rollback

kubectl rollout undo deployment NAME --to-revision=5

## Servicios

kubectl get svc -l app=front
kubectl describe svc my-service
kubectl get endpoints

## Namespace

kubectl get namespace
kubectl get pods --namespace=<insert-namespace-name-here>
kubectl run NAME --image=nginx:alpine --namespace=<insert-namespace-name-here>
kubectl get deploy -n dev

Setting the namespace preference
kubectl config set-context --current --namespace=<insert-namespace-name-here>

# Validate it

kubectl config view --minify | grep namespace:

---

Para solucioarlo, puedes ejecutar este comando:

kubectl port-forward <pod-name> 7000:<pod-port>

Luego, solo vas a http://localhost:7000 y deberías ver tu pod!

---

\*\* Docker
Crear un container y luego levantar en un puerto
docker run --rm -dti --net host --name golang golang bash
docker run --rm -dti -p 9090:9090 --name golang -v golang bash

\*\* Crear una imagen con el archivo del proyecto
docker build -t NAME-IMAGE -f Dockerfile .

\*\* Crear el container con la imagen creada
docker run -d -p 9091:9090 --name k8s-hands-on k8s-hands-on

\*\* Eliminar un container
docker rm -fv NAME
