# 1. Análisis de CPU #
Procesos que consumen CPU: Los procesos llamados yes. Hay 3 instancias ejecutándose en segundo plano, cada una intentando consumir el 100% de un núcleo de CPU.

Comando utilizado:

```
htop

```

# 2. Análisis de procesos #
Listar los procesos activos:

```
ps aux --sort=-%cpu
```
Identificar procesos sospechosos: Los procesos sospechosos son yes > /dev/null (que saturan la CPU) y los procesos cat /dev/zero (que están llenando la memoria y el disco).

# 3. Análisis de memoria #
Comprobar el uso de memoria:

```
free -h
```

(Este comando muestra la memoria total, usada y libre en formato legible como GB o MB).

# 4. Análisis de disco #

## Estado general del disco:##

```
df -h
```

## Identificar qué directorios ocupan más espacio:##

```
du -sh /tmp/* | sort -h
```
(Este comando analiza la carpeta /tmp, que es donde el script malicioso ha volcado los archivos).

# 5. Diagnóstico #

¿Qué está causando el problema? Una ejecución descontrolada de un script de prueba de estrés que no fue detenido.

¿Qué tipo de procesos están afectando al sistema?

Procesos de cálculo infinito: yes genera un bucle de escritura que satura los ciclos de reloj de la CPU.

Procesos de I/O (Entrada/Salida): cat y dd están realizando escrituras masivas de ceros (/dev/zero) hacia el almacenamiento, agotando el ancho de banda del disco y el espacio disponible.

# 6. Solución #
A. Detener los procesos problemáticos
Para eliminar todos los procesos de golpe por su nombre:

```
killall yes
killall cat

```

B. Liberar memoria y eliminar archivos innecesarios
Debemos borrar los archivos de 300MB y la carpeta de pruebas creada por el script:

```
rm /tmp/mem_test1 /tmp/mem_test2
rm -rf /tmp/test_disk

```

## 7. Verificación ##
Comprobar la normalidad:

```
uptime
```

El "load average" muestra una tendencia a la baja (hacia 0.00).

```
free -h
df -h
```
Verificar que el espacio en /tmp se ha liberado y la memoria RAM disponible ha aumentado.

# Resumen #

El sistema presentaba una degradación crítica debido a procesos zombie/infinitos generados por el script de mantenimiento. Tras identificar los PIDs mediante ps aux y verificar el llenado de la partición /tmp con df, se procedió a la terminación forzosa de los procesos y la purga de archivos temporales, restaurando la estabilidad del servidor.