# install-flink-in-k8s
install flink in k8s

# HOW TO USE
```sh
git clone https://github.com/fightinggg/install-flink-in-k8s.git
cd install-flink-in-k8s
kubectl create -f flink-configuration-configmap.yaml
kubectl create -f jobmanager-service.yaml
kubectl create -f jobmanager-session-deployment-non-ha.yaml
kubectl create -f taskmanager-session-deployment.yaml
```

```sh
s@s install-flink-in-k8s % kubectl get all
NAME                                     READY   STATUS    RESTARTS   AGE
pod/flink-jobmanager-5fc59cf75b-f9kph    1/1     Running   0          4h15m
pod/flink-taskmanager-79f4bfb5b4-cxfqs   1/1     Running   0          4h14m
pod/flink-taskmanager-79f4bfb5b4-zmhdz   1/1     Running   0          4h14m

NAME                       TYPE        CLUSTER-IP    EXTERNAL-IP   PORT(S)                                        AGE
service/flink-jobmanager   NodePort    10.98.67.37   <none>        6123:30078/TCP,6124:31193/TCP,8081:31542/TCP   4h18m
service/kubernetes         ClusterIP   10.96.0.1     <none>        443/TCP                                        4h45m

NAME                                READY   UP-TO-DATE   AVAILABLE   AGE
deployment.apps/flink-jobmanager    1/1     1            1           4h15m
deployment.apps/flink-taskmanager   2/2     2            2           4h14m

NAME                                           DESIRED   CURRENT   READY   AGE
replicaset.apps/flink-jobmanager-5fc59cf75b    1         1         1       4h15m
replicaset.apps/flink-taskmanager-79f4bfb5b4   2         2         2       4h14m
# then I can use flink in localhost://31542
```
