#    clase 4
26-07-2021

En la clase de hoy vimos la presentación de git hub, es decir, una hoja de vida que empresas o reclutadores revisan para contratar, por eso es tan importante tener organizado nuestro git hub como una hoja de vida para nuestra vida profesional y para que nos conozcan. 

Tambien repasamos que era un contenedor y una imagen:

* Contenedor: es como un recipiente que esta corriendo nuestra aplicacion, donde tiene estados puede ser dedtenido puede ser reiniciado.
* Imagenes: las imagenes no pueden ser modificadas despues de creadas, si se crean se agrega una capa adicionando las modificaciones que hemos hecho.

Empezamos creando ficheros compose donde creamos la carpeta para el proyecto

```mkdir proxy```

Creamos y editamos el archivo Compose

```vim docker-compose.yml```

```version: '3'
services:
  web:
    image: dockercloud/hello-world
  lb:
    image: dockercloud/haproxy
    links:
      - web
    volumes:
      - /var/run/docker.sock:/var/run/docker.sock
    ports:
      - 80:80
```

Utilizamos los siguientes comandos

```docker-compose up -d```

```docker-compose ps```

Para conectarnos al servidor tenemos primero que saber nuestra ip con el siguiente comando pude saber mi ip:

```ip a s```

Al saber nuestra ip escribimos la direccion en nuestro navegador web y entramos a nuestro servidor. Cuando ya deseamos apagar el servicio se escribe el siguiente comando:

```docker-compose down```

Tambien vimos y creamos jenkins asi que empezamos creando una carpeta llamada jenkins

```mkdir jenkins```

Nos paramos en la carpeta que creamos

```cd jenkins/```

Despues clonamos el archivo que esta en git hub

```git clone https://github.com/jsgiraldoh/Jenkins.git```

Ya con el archivo jekins nuestro siguiente paso es especificar para descarga nuestra imagen jekins 

```docker-compose -f docker-compose-jenkins.yml up -d```

Para que no tengamos problemas al momento de utilizar el archivo jenkins pues le damos permisos para no tener problemas

```sudo chown jaime:jaime jenkins_home/```

```chmod 2777 jenkins_home/```

Al momento de darle los permisos, escribimos el siguiente codigo para que nos de una contraseña y podamos seguir con la instalacion

```docker logs -f jenkins```

copiamos la contraseña que nos da jenkins y la pegamos en el servicio donde entramos con la ip y puerto 80:90 y se empieza a instalar y al final podremos registrarnos y entrar a jekins. Cuando queramos apagar el servicio escribimos el siguiente comando:

```docker-compose -f docker-compose-jenkins.yml down```



