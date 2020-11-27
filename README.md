# Sample cluster with 1 controller and 2 workers

# Prerequisites:
You need to install vagrant and virtualbox in advance for this to work.

# Usage:
For starting the cluster you can do it by running:
```
./up.sh
```
I recommend that you take a look at the `up.sh` to know what it does, then the `Vagrantfile` and then each script to see how you can quickly bootstrap a functional cluster (not production ready, but functional), also be aware that you will need at least 6 Gbs of free memory for the virtual machines.


Coy the kubeconfig to your machine, export its path as an environment variable and test it (give it at least 5 mins for the machines to boot, install everything and are running, you can watch the vagrant log).
```
vagrant ssh cluster1-master1 -c "sudo cat /root/.kube/config" > vagrant-kubeconfig
export KUBECONFIG="$(pwd)/vagrant-kubeconfig"
```

And then test it:
```
❯ kubectl get pods -A -o wide
NAMESPACE     NAME                                       READY   STATUS             RESTARTS   AGE   IP                NODE               NOMINATED NODE   READINESS GATES
default       web-test-2-594487698d-zz2wd                1/1     Running            0          57m   10.44.0.2         cluster1-worker1   <none>           <none>
default       web-test-6c77dcfbc-c97bw                   1/1     Running            0          57m   10.36.0.8         cluster1-worker2   <none>           <none>
default       web-test-6c77dcfbc-j84gn                   1/1     Running            0          57m   10.36.0.7         cluster1-worker2   <none>           <none>
default       web-test-6c77dcfbc-km49j                   1/1     Running            0          57m   10.44.0.3         cluster1-worker1   <none>           <none>
development   web-dev-shop-5cc79c745c-p7snd              1/1     Running            0          57m   10.36.0.1         cluster1-worker2   <none>           <none>
development   web-dev-shop-dev2-679468cd95-l8sw7         1/1     Running            0          57m   10.36.0.2         cluster1-worker2   <none>           <none>
...
```
You should see something like that, it means your cluster is up and running and it is fully functional.

NOTE: This is purely educational, USE AT YOUR OWN RISK.

This is based in this [repo](https://github.com/wuestkamp/cka-example-environments)

For more info to there and if you are practicing for the CKA you can go to: [https:/killer.sh](https:/killer.sh)
