# Ejercicio2

Creamos un nuevo namespace para este ejercicio 

*k create ns practica3-2*

Creamos tanto el stateful set con la configuración de mongodb y el servicio para exponer los pods 

*k create -f service.yaml -n practica3-2*

*k apply -f statefulset.yaml -n practica3-2*

<img src="https://raw.githubusercontent.com/ariane10/kube-exercises/main/hw-03/answer_exercise_2/capturas/Imagen2_1.png" height="150px">

Accedemos a mongod-0 que será el pod administrador

*k exec -it mongod-0 -n practica3-2 bash*

Y lanzamos el siguiente comando para generar el conjunto de replicas

rs.initiate ( { _id: "MainRepSet", version: 1, members: [{_id: 0, host: "mongod-0.mongodb-service.default.svc.cluster.local:27017" }, {_id: 1, host: "mongod-1.mongodb-service.default.svc.cluster.local:27017" }, {_id: 2, host: "mongod-2.mongodb-service.default.svc.cluster.local:27017" } ]});

Al lanzar este comando me ha salido el siguiente error que se ve en la imagen y no he podido continuar con la configuración de las instancias.

<img src="https://raw.githubusercontent.com/ariane10/kube-exercises/main/hw-03/answer_exercise_2/capturas/Imagen2_2.png" height="100px">

## Replicaset VS StatefulSet

La diferencia entre replicaset y statefulset es que el statefulset es para aplicaciones con estado, donde importa la identidad de un Pod y replicaset en cambio no. 

El replicaset nombra los pods con el nombre del replicaset + hash a la hora de la creación + hash aleatorio. El problema es que, si cambia la configuración, por ejemplo, si un pod muere, cuando se crea otro lo hace con un nombre aleatorio diferente y ya no sabrás a cuál hacer referencia.

StatefulSet crea una serie de pods en orden y en realidad los numera, por ejemplo, mongod-0, mongod-1, mongod-2, etc. Si los reemplaza porque la configuración cambia, mantiene los nombres iguales.

Por lo que en este ejercicio afectaria a la configuración cuando se hace referencia a un pod, ya que si alguno de los pods cambiara y se crearia otro en su lugar, ya no se haria referencia al mismo, tendría otro nombre.


