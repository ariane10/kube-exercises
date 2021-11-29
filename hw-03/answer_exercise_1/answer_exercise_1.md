
# Ejercicio 1

## Exponer nginx en el dominio http

Creamos el namespace para que la zona de trabajo esté aislada del resto

*k create namespace practica3*

Creamos el deployment 

*k create -f deployment.yaml -n practica3*

<img src="https://raw.githubusercontent.com/ariane10/kube-exercises/main/hw-03/answer_exercise_1/capturas/Imagen1_1.png" height="150px">

Creamos un service del tipo clusterIP exponiendo los pods

*k expose deploy nginx-deployment -n practica3 --name=nginx-service --port 8080 --target-port 80* 

<img src="https://raw.githubusercontent.com/ariane10/kube-exercises/main/hw-03/answer_exercise_1/capturas/Imagen1_2.png" height="80px">

Creamos un ingress controller para acceder a nuestro servicio a través del dominio "ariane.gutierrez.student.lasalle.com"

*k create -f ingress.yaml -n practica3*

<img src="https://raw.githubusercontent.com/ariane10/kube-exercises/main/hw-03/answer_exercise_1/capturas/Imagen1_3.png" height="100px">

Ejecutamos *minikube service nginx-service -n practica3* para ver en que IP se está exponiendo nuestro servicio y modificamos el fichero hosts ubicado en /private/etc con esa IP apuntando al dominio. 

<img src="https://raw.githubusercontent.com/ariane10/kube-exercises/main/hw-03/answer_exercise_1/capturas/Imagen1_4.png" height="200px">
<img src="https://raw.githubusercontent.com/ariane10/kube-exercises/main/hw-03/answer_exercise_1/capturas/Imagen1_5.png" height="200px">

## Exponer nginx en el dominio https

Para la segunda parte del ejercicio creamos un certificado SSL y creamos un secret que contenga el certificado. 

<img src="https://raw.githubusercontent.com/ariane10/kube-exercises/main/hw-03/answer_exercise_1/capturas/Imagen1_6.png" height="200px">

<img src="https://raw.githubusercontent.com/ariane10/kube-exercises/main/hw-03/answer_exercise_1/capturas/Imagen1_7.png" height="200px">

Actualizamos el ingress con el certificado que acabamos crear.

<img src="https://raw.githubusercontent.com/ariane10/kube-exercises/main/hw-03/answer_exercise_1/capturas/Imagen1_8.png" height="200px">
<img src="https://raw.githubusercontent.com/ariane10/kube-exercises/main/hw-03/answer_exercise_1/capturas/Imagen1_9.png" height="200px">
<img src="https://raw.githubusercontent.com/ariane10/kube-exercises/main/hw-03/answer_exercise_1/capturas/Imagen1_10.png" height="200px">
<img src="https://raw.githubusercontent.com/ariane10/kube-exercises/main/hw-03/answer_exercise_1/capturas/Imagen1_11.png" height="200px">





