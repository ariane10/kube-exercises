# Ejercicio 3

Creamos un nuevo espacio de trabajo 

*k create nd practica3-3*

Para este ejercicio usaremos el mismo deployment del ejercicio1, pero se ha cambiado el tamaño de la cpu a 2m para el escalado de las replicas.

Creamos el deployment, el servicio y el nuevo objeto HPA

*k apply -f hpa.yaml -n practica3-3*

<img src="https://raw.githubusercontent.com/ariane10/kube-exercises/main/hw-03/answer_exercise_3/capturas/Imagen3-1.png" height="150px">


Lanzamos el siguiente comando para hacer una prueba de estres sobre la aplicación: 

*kubectl run -i --tty load-generator --rm --image=busybox --restart=Never -n practica3-3 -- /bin/sh -c "while sleep 0.01; do wget -q -O- http://nginx-service; done"*

En esta primera imagen se puede ver que se ha generado otra replica del deployment, por lo que se ha duplicado la cantidad de pods 
<img src="https://raw.githubusercontent.com/ariane10/kube-exercises/main/hw-03/answer_exercise_3/capturas/Imagen3_2.png" height="200px">

Y en esta segunda imagen lo mismo, pero está vez al número máximo de replicas, que son 10. 
<img src="https://raw.githubusercontent.com/ariane10/kube-exercises/main/hw-03/answer_exercise_3/capturas/Imagen3_3.png" height="200px">

