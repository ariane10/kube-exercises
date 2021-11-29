# Ejercicio 3

Creamos un nuevo espacio de trabajo 

*k create nd practica3-3*

Para este ejercicio usaremos el mismo deployment del ejercicio1
Creamos el deployment, el servicio y el nuevo objeto hpa

*k apply -f hpa.yaml -n practica3-3*

<img src="https://raw.githubusercontent.com/ariane10/kube-exercises/main/hw-03/answer_exercise_3/capturas/Imagen3-1.png" height="150px">


Lanzamos el siguiente comando para hacer una prueba de estres sobre la aplicación: 

*kubectl run -i --tty load-generator --rm --image=busybox --restart=Never -n practica3-3 -- /bin/sh -c "while sleep 0.01; do wget -q -O- http://nginx-service; done"*

<img src="https://raw.githubusercontent.com/ariane10/kube-exercises/main/hw-03/answer_exercise_3/capturas/Imagen3-2.png" height="150px">

<img src="https://raw.githubusercontent.com/ariane10/kube-exercises/main/hw-03/answer_exercise_3/capturas/Imagen3-3.png" height="150px">

