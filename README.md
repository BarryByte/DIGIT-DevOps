# This is my DIGIT - Project
Section 0 : Quickstart Setup 
  * Choose infra
  * Deployment 
# k3d Cluster Setup with Data Persistence

This guide will help you set up a Kubernetes cluster using k3d with a single master node and two worker nodes (agents). Additionally, it will demonstrate how to mount a directory for data persistence and provide instructions for verifying the cluster setup.

## Prerequisites
- [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/)
- [k3d](https://k3d.io/#installation)

## Steps

1. Create a k3d cluster with a single master node and 2 agents (worker nodes), and mount the directory for data persistence. Replace `<user_name>` with your username and update the directory path accordingly.

```bash
k3d cluster create --k3s-server-arg "--no-deploy=traefik" --agents 2 -v "/home/<user_name>/kube:/kube@agent[0,1]" -v "/home/<user_name>/kube:/kube@server[0]" --port "80:80@loadbalancer"
```

## Once the cluster creation is successful, obtain the kubeconfig file to connect to the cluster.
```
k3d kubeconfig get k3s-default > myk3dconfig
export KUBECONFIG=<path-to-your-kube_config>
kubectl config use-context k3d-k3s-default --kubeconfig=myk3dconfig
 ```
## Verify the cluster creation by running the following commands:

```
kubectl cluster-info
```



## Conclusion
You have successfully set up a k3d cluster with data persistence and verified its status. You can now proceed with deploying workloads and managing your Kubernetes cluster.

![Screenshot from 2024-03-28 17-43-05](https://github.com/BarryByte/DIGIT-DevOps/assets/145528099/a5dac03b-2b1d-4f61-8fe7-6018712f1e07)
![Screenshot from 2024-03-28 17-28-06](https://github.com/BarryByte/DIGIT-DevOps/assets/145528099/138a0f57-1468-4ea5-99b1-330a26a3bcd4)
![Screenshot from 2024-03-28 17-27-37](https://github.com/BarryByte/DIGIT-DevOps/assets/145528099/5d3d0e8c-bb76-4745-a23e-2096f36834ff)
![Screenshot from 2024-03-28 17-27-46](https://github.com/BarryByte/DIGIT-DevOps/assets/145528099/f891afaf-3fe0-43e8-b435-9452f7b7ce0d)
![Screenshot from 2024-03-26 23-03-06](https://github.com/BarryByte/DIGIT-DevOps/assets/145528099/6f256815-f4e6-4ef0-899d-ebd7b23ac461)
![Screenshot from 2024-03-26 23-00-07](https://github.com/BarryByte/DIGIT-DevOps/assets/145528099/a68e1773-e053-4982-b458-6d3c0c2df635)





