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

# gcloud compute disks create --size 200GB mysql-disk
