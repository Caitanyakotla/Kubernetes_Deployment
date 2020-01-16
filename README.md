# Kubernetes

When you use kubectl autoscale, you specify a maximum and minimum number of replicas for your application, as well as a CPU utilization target. For example, to set the maximum number of replicas to six and the minimum to four, with a CPU utilization target of 50% utilization, run the following command:

kubectl autoscale deployment my-app --max 6 --min 4 --cpu-percent 50
In this command, the --max flag is required. The --cpu-percent flag is the target CPU utilization over all the Pods. This command does not immediately scale the Deployment to six replicas, unless there is already a systemic demand.

After running kubectl autoscale, the HorizontalPodAutoscaler object is created and targets the application. When there a change in load, the object increases or decreases the application's replicas.

Deployment:
Deployment is the easiest and most used resource for deploying your application. It is a Kubernetes controller that matches the current state of your cluster to the desired state mentioned in the Deployment manifest. e.g. If you create a deployment with 1 replica, it will check that the desired state of ReplicaSet is 1 and current state is 0, so it will create a ReplicaSet, which will further create the pod. If you create a deployment with name counter, it will create a ReplicaSet with name counter-<replica-set-id>, which will further create a Pod with name counter-<replica-set->-<pod-id>.
Deployments are usually used for stateless applications. However, you can save the state of deployment by attaching a Persistent Volume to it and make it stateful, but all the pods of a deployment will be sharing the same Volume and data across all of them will be same.
For deploying the sample counter app using a deployment, we will be using the following manifest, you can deploy it by copying the below manifest and saving it in a file e.g. deployment.yaml, and then applying by


Stateful Set:
Every replica of a stateful set will have its own state, and each of the pods will be creating its own PVC(Persistent Volume Claim). So a statefulset with 3 replicas will create 3 pods, each having its own Volume, so total 3 PVCs.
