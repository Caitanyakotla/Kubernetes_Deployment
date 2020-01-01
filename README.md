# Kubernetes

When you use kubectl autoscale, you specify a maximum and minimum number of replicas for your application, as well as a CPU utilization target. For example, to set the maximum number of replicas to six and the minimum to four, with a CPU utilization target of 50% utilization, run the following command:

kubectl autoscale deployment my-app --max 6 --min 4 --cpu-percent 50
In this command, the --max flag is required. The --cpu-percent flag is the target CPU utilization over all the Pods. This command does not immediately scale the Deployment to six replicas, unless there is already a systemic demand.

After running kubectl autoscale, the HorizontalPodAutoscaler object is created and targets the application. When there a change in load, the object increases or decreases the application's replicas.
