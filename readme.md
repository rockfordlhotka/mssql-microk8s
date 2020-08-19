# Deploy SQL Server on microk8s

Top level steps:

1. Install microk8s
1. Enable the storage service in microk8s
1. Enable the load balancer service in microk8s
1. Read [SQL Server on Linux on Kubernetes](https://www.phillipsj.net/posts/sql-server-on-linux-on-kubernetes-part-1/), especially Part 2
   1. Don't follow the instructions in the blog - just absorb the concepts
1. In this repo look at the `storage.yaml` file to see how I set up my storage volume and claim
1. In this repo look at the `deploy.yaml` file to see how I deployed the container/pod/service
