# kubernetes-Oscar-Fernandez

clono el repositorio git@github.com:jluisalvarez/k8s-vote-app.git

me posiciono en el directorio de trabajo  "k8s-vote-app"

ejecuto todos los servicio y deployments 
$ kubectl apply -f .

escalo el deployments "vote"
$ kubectl scale deployments/vote --replicas=3

