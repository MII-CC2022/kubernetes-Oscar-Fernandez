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
