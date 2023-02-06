# Mithun_Assignment
Voting App:

Created the pods as per given instructions.
Application is running with requried PODs.

[root@ip-172-31-5-254 k8s-specifications]#  kubectl get all
NAME                          READY   STATUS    RESTARTS   AGE
pod/db-b54cd94f4-hk5t7        1/1     Running   0          3h20m
pod/redis-868d64d78-gcrhr     1/1     Running   0          3h20m
pod/result-5d57b59f4b-8nfjl   1/1     Running   0          3h20m
pod/vote-94849dc97-vrlrt      1/1     Running   0          3h20m
pod/worker-dd46d7584-l8ww2    1/1     Running   0          3h20m

NAME             TYPE        CLUSTER-IP       EXTERNAL-IP   PORT(S)          AGE
service/db       ClusterIP   10.98.24.90      <none>        5432/TCP         3h20m
service/redis    ClusterIP   10.107.168.5     <none>        6379/TCP         3h20m
service/result   NodePort    10.100.101.216   <none>        5001:31001/TCP   3h20m
service/vote     NodePort    10.100.230.251   <none>        5000:31000/TCP   3h20m

NAME                     READY   UP-TO-DATE   AVAILABLE   AGE
deployment.apps/db       1/1     1            1           3h20m
deployment.apps/redis    1/1     1            1           3h20m
deployment.apps/result   1/1     1            1           3h20m
deployment.apps/vote     1/1     1            1           3h20m
deployment.apps/worker   1/1     1            1           3h20m

NAME                                DESIRED   CURRENT   READY   AGE
replicaset.apps/db-b54cd94f4        1         1         1       3h20m
replicaset.apps/redis-868d64d78     1         1         1       3h20m
replicaset.apps/result-5d57b59f4b   1         1         1       3h20m
replicaset.apps/vote-94849dc97      1         1         1       3h20m
replicaset.apps/worker-dd46d7584    1         1         1       3h20m

Deleted Voting pod: kubectl delete pod vote-94849dc97-vrlrt
NAME                          READY   STATUS    RESTARTS   AGE
pod/db-b54cd94f4-hk5t7        1/1     Running   0          3h24m
pod/redis-868d64d78-gcrhr     1/1     Running   0          3h24m
pod/result-5d57b59f4b-8nfjl   1/1     Running   0          3h24m
pod/vote-94849dc97-4jq2s      1/1     Running   0          30s
pod/worker-dd46d7584-l8ww2    1/1     Running   0          3h24m
>> On deleting voting pod, it spawned immediately and application was NOT impacted.

Deleted Worker pod:kubectl delete pod worker-dd46d7584-l8ww2
NAME                          READY   STATUS    RESTARTS   AGE
pod/db-b54cd94f4-hk5t7        1/1     Running   0          3h24m
pod/redis-868d64d78-gcrhr     1/1     Running   0          3h24m
pod/result-5d57b59f4b-8nfjl   1/1     Running   0          3h24m
pod/vote-94849dc97-4jq2s      1/1     Running   0          86s
pod/worker-dd46d7584-c6s6j    1/1     Running   0          14s
>> On deleting worker pod, it spawned again and application was NOT impacted.

Deleted db pod:
On deleting DB pod, until new DB POD was spawned, the results were not being captured.
Also, worked pod was also restarted after DB pod was deleted.
Then application continued to work fine when DB pod was up.
