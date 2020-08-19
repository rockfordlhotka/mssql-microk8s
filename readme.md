# Deploy SQL Server on microk8s

Top level steps:

1. Install microk8s
1. Enable the storage service in microk8s
1. Enable the load balancer service in microk8s
1. Read [Deploy a SQL Server container in Kubernetes](https://docs.microsoft.com/en-us/sql/linux/tutorial-sql-server-containers-kubernetes?view=sql-server-ver15)
   1. Don't follow the instructions - just absorb the concepts
   1. **Except:** do step 1 to _Create an SA password_: `kubectl create secret generic mssql --from-literal=SA_PASSWORD="MyC0m9l&xP@ssw0rd"`
1. Read [SQL Server on Linux on Kubernetes](https://www.phillipsj.net/posts/sql-server-on-linux-on-kubernetes-part-1/), especially Part 2
   1. Don't follow the instructions in the blog - just absorb the concepts
1. In this repo look at the `storage.yaml` file to see how I set up my storage volume and claim
1. In this repo look at the `deploy.yaml` file to see how I deployed the container/pod/service

Notes:

* I have a specific amd64 node called "acer01"; you will need to remove that restriction from the `deploy.yaml` file
* You should leave the `kubernetes.io/arch` node selector so the pod _does_ run on an amd64 node (I have a mix of amd64 and arm64 nodes in my cluster)
* The `containerinit` pod is temporary, and is necessary because mssql doesn't run as root, and it is necessary to set the file permissions in the persistent volume so the mssql user can use the file system

