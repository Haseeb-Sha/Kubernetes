- minikube start --driver docker :(starts control plane node container)
- kubectl get no

# KUBE COMMMADS
  - CRUD
     kubectl create namespace name ( or use config file)

     kubectl scale --replica=0 statefulset/mongodb

  - status
      kubectl get deployment nginx-deployment -o yaml (to get status from etcd)
      kubectl get all
      kubectl api-resources --namespaced=false  ( check reosuces that are not namespace bounded)
      kubectl get ns

      kubectl get pvc
      kubectl get ingress -n namespace

      kubectl config set-context --current --namespace=namespace_name (set all commands to use this namespace) or use kubectx and kubens
      kubens name_space
 
      kubectl get endpoints (which pods are the endpoints of the service)

      kubectl port-forward service/mongo-express-service 8081:8081

  - debugging
      kubectl describe service service_name (check endpoints it should match the pod Ip's)
      kubectl cluster-info

  - minikube
      minikube addons enable ingress
      minikube dashboard
  - helm
        helm repo add bitnami url
        helm search repo bitnami/chart_name
        helm install chart_name
        helm install name --values=my-values.yaml <repo/chart_name>
        helm upgrade <chart_name>
        helm rollback <chart_name>
        helm ls 
        helm uninstall mongodb
        
# used to access only single repo in the ecr but one line comment
  - create docker login (for ecr) 
    kubectl create secret docker-registry name \
    --docker-server=https://.. \
    --docker-username=AWS \
    --docker-password=

-> create secrets & config first then use it in deployment
-> node port ranges from 30000 to 32767
-> namespaces are virtual cluster inside a cluster 
-> configmap and secrets are not shared between namespaces 
-> however services can be shared between namespaces using service-name.namespace
-> volume and nodes cannot be created in the namespace
-> if you want to use multiple port service use different names for that in deployment and service files
-> use cluserIP to none if you want to use direct connect pod for stateful application in service file (headless service)
-> pvc claim should bne in the same namespace as of deployment

-> we can also mount local volumes to our pod and container to use that files for the image using configMap and Secrets
     

