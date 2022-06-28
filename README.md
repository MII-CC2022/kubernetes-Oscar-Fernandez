# kubernetes-Oscar-Fernandez

clono el repositorio git@github.com:jluisalvarez/k8s-vote-app.git

me posiciono en el directorio de trabajo  "k8s-vote-app"

ejecuto todos los servicio y deployments 
$ kubectl apply -f .

escalo el deployments "vote"
$ kubectl scale deployments/vote --replicas=3

actualizar de version de "vote" y "result" cambiando la imagen del deployment con la nueva imagen con etiqueta "after"
$ kubectl set image deployments/result result=dockersamples/examplevotingapp_result:after
$ kubectl set image deployments/vote vote=dockersamples/examplevotingapp_vote:after

para volver a la ultima version de trabajo
$ kubectl rollout undo deployments/vote 
$ kubectl rollout undo deployments/result 

ver descripcion detallada de los deployments
$ kubectl get deployments -o wide

Ejemplo de los deploy luego de probar las distintas funciones
NAME     READY   UP-TO-DATE   AVAILABLE   AGE    CONTAINERS   IMAGES                                        SELECTOR
db       1/1     1            1           175m   postgres     postgres:9.4                                  app=db
redis    1/1     1            1           175m   redis        redis:alpine                                  app=redis
result   1/1     1            1           175m   result       dockersamples/examplevotingapp_result:after   app=result
vote     3/3     3            3           175m   vote         dockersamples/examplevotingapp_vote:before    app=vote
worker   1/1     1            1           175m   worker       dockersamples/examplevotingapp_worker         app=worker

Ejemplo de los pods
NAME                      READY   STATUS    RESTARTS   AGE
db-5f5d945476-h6dbn       1/1     Running   0          3h
redis-67db9bd79b-w65d5    1/1     Running   0          3h
result-5694bcc568-7tlqc   1/1     Running   0          7m30s
vote-6d4876585f-5bnr4     1/1     Running   0          5m26s
vote-6d4876585f-sp85t     1/1     Running   0          5m27s
vote-6d4876585f-tl9dj     1/1     Running   0          5m29s
worker-7cbf9df499-wrmbm   1/1     Running   0          3h
