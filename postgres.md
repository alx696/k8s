```
$ kubectl get pods
$ kubectl exec -it postgres-deployment-c569f5479-lfg6k bash
```
进入Pod执行：
```
# echo "host all all all trust" >> /var/lib/postgresql/data/pgdata/pg_hba.conf
# exit
```
缩放以让Pod重建：
```
$ kubectl scale -n default deployment postgres-deployment --replicas=0
$ kubectl get pods
```
等待直到`postgres-deployment-`开头的Pod没有了，执行：
```
$ kubectl scale -n default deployment postgres-deployment --replicas=1
$ kubectl scale -n default deployment postgres-deployment --replicas=2
```