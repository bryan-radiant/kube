# Creating dev cluster with Kube

Create the dev cluster
```
gcloud alpha container clusters create dev-tbmatch --num-nodes 2 --network dev
Creating cluster dev-tbmatch...done.
Created [https://www.googleapis.com/container/v1beta1/projects/radiant-cloud/zones/us-central1-a/clusters/dev-tbmatch].
Using gcloud compute copy-files to fetch ssl certs from cluster master...
Warning: Permanently added '130.211.141.229' (ECDSA) to the list of known hosts.
kubecfg.key                                                                                                                  100% 1675     1.6KB/s   00:00    
kubecfg.crt                                                                                                                  100% 1139     1.1KB/s   00:00    
ca.crt                                                                                                                       100% 1172     1.1KB/s   00:01    
kubeconfig entry generated for dev-tbmatch. To switch context to the cluster, run

$ kubectl config use-context gke_radiant-cloud_us-central1-a_dev-tbmatch

NAME         ZONE           CLUSTER_API_VERSION  MASTER_IP        MACHINE_TYPE                           NODES  STATUS
dev-tbmatch  us-central1-a  0.18.2               130.211.141.229  n1-standard-1, container-vm-v20150505  2      running
```

Create the pod
```
kubectl create -f tbfe.yaml
```

Create the service
```
kubectl create -f tbfe-service.yaml
```

# Creating disks

```
gcloud compute disks create --size 200GB mysql-disk
```

# Creating emailrelay image

Build the image from the ops repo.
```
make dockimg-build-emailrelay
```

Tag the image.
```
docker tag localhost:5000/emailrelay gcr.io/radiant-cloud/emailrelay
```

*Optional*: You may need to install gcloud preview, this will kick off the install process for you:
```
cloud preview docker
```

Push the image up to the repo.
```
gcloud preview docker push gcr.io/radiant-cloud/emailrelay
```
