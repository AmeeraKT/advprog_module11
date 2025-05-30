# Advanced Programming Module 11

## Deploymnent on Kubernetes

#### Reflection 1: 

1. Compare the application logs before and after you exposed it as a Service. Try to open the app several times while the proxy into the Service is running. What do you see in the logs? Does the number of logs increase each time you open the app?


2. Notice that there are two versions of `kubectl get` invocation during this tutorial section. The first does not have any option, while the latter has `-n` option with value set to `kube-system`. What is the purpose of the `-n` option and why did the output not list the pods/services that you explicitly created?
The `-n` option specifies the namespace of the Kubernetes services and pods to be
retrieved from. When running `kubectl get pods` there was no output because they
are in the default namespace meanwhile running `kubectl get pods -n kube-system`
gets all resources that are under the kube-system namespace. 


#### Reflection 2:

1. What is the difference between Rolling Update and Recreate deployment strategy?
```
The Rolling Update strategy updates one pod at a time while letting the old pods run.
As the update creates new pods, it lets the old ones run. When the new pods are ready,
the old pods are deleted then a new pod is created and this process repeats until all
the pods are updated.
On the other hand, the Recreate development shuts down all pods at once, stopping the
application. Then new pods are created during the update.
```

2.  Try deploying the Spring Petclinic REST using Recreate deployment strategy and document your attempt.

3. Prepare different manifest files for executing Recreate deployment strategy.
4. What do you think are the benefits of using Kubernetes manifest files? Recall your experience in deploying the app manually and compare it to your experience when deploying the same app by applying the manifest files (i.e., invoking `kubectl apply -f` command) to the cluster.

5. (Optional) Do the same tutorial steps, but on a managed Kubernetes cluster (e.g., GCP). You need to provision a Kubernetes cluster on Google Cloud Platform. Then, re-run the tutorial steps (Hello Minikube and Rolling Update) on the remote cluster. Document your attempt and highlight the differences and any issues you encountered.

