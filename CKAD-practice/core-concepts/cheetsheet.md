### Context & Configuration

```
#Show Merged kubeconfig settings.
kubectl config view 

kubectl config view -o jsonpath='{.users[].name}'    # display the first user
kubectl config view -o jsonpath='{.users[*].name}'   # get a list of users
kubectl config get-contexts                          # display list of contexts
kubectl config current-context                       # display the current-context

# permanently save the namespace for all subsequent kubectl commands in that context.
kubectl config set-context --current --namespace=ggckad-s2

```

### Creating Objects

```
kubectl apply -f busybox.yaml
kubectl apply -f nginx.yaml

# create a Job which prints "Hello World"
kubectl create job hello --image=busybox:1.28 -- echo "Hello World"

# create a CronJob that prints "Hello World" every minute
kubectl create cronjob hello --image=busybox:1.28   --schedule="*/1 * * * *" -- echo "Hello World"

```

### viewing & finding resources

```
get commands with basic outputs
kubectl get pods # list all pods of all namespaces
kubect get services # list all services of all namespaces
kubectl get deployments # list all deployments of all namespaces

kubectl get pods --namespace=<my-namespace> # list all pods of a given namespaces
kubect get services --namespace=<my-namespace> # list all services of a given namespaces
kubectl get deployments --namespace=<my-namespace> # list all deployments of a given namespaces

kubectl get pod/<pod-name> --namespace=<my-namespace> # get only the pod which match the pod name from a given namespace. similarly we can apply things for deployments and services also

kubectl get pod/<pod-name> --namespace=<my-namespace> -o wids # more details with respect ot a single given pod

kubectl describe pod/<pod-name>  # describes lot of details with respect ot the pod

```