Задача 1: Установить Minikube

root@kuber1:/home/admin# minikube status
minikube
type: Control Plane
host: Running
kubelet: Running
apiserver: Running
kubeconfig: Configured

root@kuber1:/home/admin# kubectl get pods --namespace=kube-system
NAME                             READY   STATUS    RESTARTS   AGE
coredns-64897985d-qjh46          0/1     Running   0          27s
etcd-kuber1                      1/1     Running   0          39s
kube-apiserver-kuber1            1/1     Running   0          39s
kube-controller-manager-kuber1   1/1     Running   0          39s
kube-proxy-v9pz2                 1/1     Running   0          27s
kube-scheduler-kuber1            1/1     Running   0          39s
storage-provisioner              1/1     Running   0          37s

Задача 2: Запуск Hello World

root@kuber1:/home/admin# minikube dashboard
* Enabling dashboard ...
  - Using image kubernetesui/dashboard:v2.3.1
  - Using image kubernetesui/metrics-scraper:v1.0.7
* Verifying dashboard health ...
* Launching proxy ...
* Verifying proxy health ...
http://127.0.0.1:41123/api/v1/namespaces/kubernetes-dashboard/services/http:kubernetes-dashboard:/proxy/



root@kuber1:/home/admin# minikube addons list
|-----------------------------|----------|--------------|--------------------------------|
|         ADDON NAME          | PROFILE  |    STATUS    |           MAINTAINER           |
|-----------------------------|----------|--------------|--------------------------------|
| ambassador                  | minikube | disabled     | third-party (ambassador)       |
| auto-pause                  | minikube | disabled     | google                         |
| csi-hostpath-driver         | minikube | disabled     | kubernetes                     |
| dashboard                   | minikube | enabled ✅   | kubernetes                     |
| default-storageclass        | minikube | enabled ✅   | kubernetes                     |
| efk                         | minikube | disabled     | third-party (elastic)          |
| freshpod                    | minikube | disabled     | google                         |
| gcp-auth                    | minikube | disabled     | google                         |
| gvisor                      | minikube | disabled     | google                         |
| helm-tiller                 | minikube | disabled     | third-party (helm)             |
| ingress                     | minikube | enabled ✅   | unknown (third-party)          |
| ingress-dns                 | minikube | disabled     | google                         |
| istio                       | minikube | disabled     | third-party (istio)            |
| istio-provisioner           | minikube | disabled     | third-party (istio)            |
| kong                        | minikube | disabled     | third-party (Kong HQ)          |
| kubevirt                    | minikube | disabled     | third-party (kubevirt)         |
| logviewer                   | minikube | disabled     | unknown (third-party)          |
| metallb                     | minikube | disabled     | third-party (metallb)          |
| metrics-server              | minikube | disabled     | kubernetes                     |
| nvidia-driver-installer     | minikube | disabled     | google                         |
| nvidia-gpu-device-plugin    | minikube | disabled     | third-party (nvidia)           |
| olm                         | minikube | disabled     | third-party (operator          |
|                             |          |              | framework)                     |
| pod-security-policy         | minikube | disabled     | unknown (third-party)          |
| portainer                   | minikube | disabled     | portainer.io                   |
| registry                    | minikube | disabled     | google                         |
| registry-aliases            | minikube | disabled     | unknown (third-party)          |
| registry-creds              | minikube | disabled     | third-party (upmc enterprises) |
| storage-provisioner         | minikube | enabled ✅   | google                         |
| storage-provisioner-gluster | minikube | disabled     | unknown (third-party)          |
| volumesnapshots             | minikube | disabled     | kubernetes                     |
|-----------------------------|----------|--------------|--------------------------------|


root@kuber1:/home/admin# minikube service --all
* service default/kubernetes has no node port
|-----------|------------|--------------|--------------------------|
| NAMESPACE |    NAME    | TARGET PORT  |           URL            |
|-----------|------------|--------------|--------------------------|
| default   | hello-node |         8080 | http://10.128.0.20:31211 |
| default   | kubernetes | No node port |
|-----------|------------|--------------|--------------------------|


Задача 3: Установить kubectl

root@kuber1:/home/admin# kubectl get services
NAME         TYPE           CLUSTER-IP      EXTERNAL-IP   PORT(S)          AGE
hello-node   LoadBalancer   10.106.133.49   <pending>     8080:31211/TCP   20m
kubernetes   ClusterIP      10.96.0.1       <none>        443/TCP          63m
