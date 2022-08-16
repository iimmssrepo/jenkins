# jenkins installation with helm

https://www.jenkins.io/doc/book/installing/kubernetes/

$ kubectl create namespace jenkins

$ helm repo add jenkinsci https://charts.jenkins.io
$ helm repo update

$ kubectl apply -f jenkins-volume.yaml

## En minikube:
# minikube ssh
# sudo chown -R 1000:1000 /data/jenkins-volume
## En Docker Desktop:
# docker run -it --rm --privileged --pid=host justincormack/nsenter1
# chown -R 1000:1000 /containers/services/docker/rootfs/data/jenkins-volume

$ kubectl apply -f jenkins-sa.yaml

$ helm install jenkins -n jenkins -f jenkins-values.yaml jenkinsci/jenkins
