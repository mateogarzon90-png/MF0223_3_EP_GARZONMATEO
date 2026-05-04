# Error al crear el docker tal cual se ha facilitado:#

PS C:\Users\Matins\Desktop\MF0223_3_EP_1_GarzonMateo> docker-compose up -d
yaml: construct errors:
  line 12: mapping key "volumes" already defined at line 6
  line 14: mapping key "networks" already defined at line 8



  # Correcciones hechas:#

  ## Remover la linea de la version ya que hoy en dia es Obsoleta. ##

  ## Persistencia del Proceso: ##
  Una imagen de Ubuntu, por defecto, ejecuta /bin/bash. Al no tener un terminal interactivo asignado en el archivo, el contenedor se detendría inmediatamente después de iniciar porque no tiene procesos en primer plano.
  Por ello se han insertado las nuevas dos lineas: 
```
  stdin_open: true 
    tty: true

```
    stdin_open : true :   Mantiene la entrada estándar abierta.
    tty: true :           Asigna un terminal virtual.

  ## Inconsistencia en Redes: ##
  Se declara el uso de net_devXX dentro del servicio, pero en la sección global se define como net_dev_XX (con un guion bajo extra). Esto causa un error de "red no encontrada".

  ## Etiqueta de Imagen: #3
  Aunque ubuntu:22 puede funcionar, la etiqueta oficial y estable es ubuntu:22.04.

# Fichero docker-compose.yml correcto y funcional: #

```

services:
  srv_dev_XX:
    image: ubuntu:22.04
    container_name: srv_dev_XX
    
    stdin_open: true 
    tty: true
    volumes:
      - datos_devXX:/var/empresa
    networks:
      - net_devXX
    ports:
      - "8090:3000"

volumes:
  datos_devXX:

networks:
  net_devXX:
    driver: bridge

```

# Autor #

Mateo Garzon

