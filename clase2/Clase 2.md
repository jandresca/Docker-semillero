# Clase 2

21/07/2021

En la clase de hoy instalamos docker en nuestra maquina virtual, asi mismo empezamos a meter el primer comando que era: 

* ```sudo apt-get update```
 
*  ```sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg \
    lsb-release```

Este comando descarga todos los paquetes index y los permisos para poder descargar docker en nuestra maquina virtual (Ubuntu). Despues de realizar este comando podemos pasar al siguiente paso que es agregar las llaves oficales de docker que es:

*  ```curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg```


----
Despues utilizamos el comando para traernos los repositorios de docker que es:

* ```echo \
  "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null```
  
 Y para que todo descargarnos esos repositorios escribimos los siguientes comandos:
 
* ```sudo apt-get update```

* ```sudo apt-get install docker-ce docker-ce-cli containerd.io```


Para verificar que todo esta funcionando bien se escribe el siguiente comando para confirmar que este correcto:

* ```sudo docker run hello-world```

---
Si no tenemos ningun error en este momento, entonces ya tenemos instalado docker ahora el siguiente paso fue instalar docker compose y empezamos con el siguiente comando:

* ```sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose```

para poder utilizar la descarga del comando anterior tenemos que darle permisos con el siguiente comando:

* ```sudo chmod +x /usr/local/bin/docker-compose```

Por ultimo para comprobar la version del docker compose escribimos el siguiente comando:

* ```docker-compose --version```



