# Administración de sistemas Linux y resolución de incidencias #

## 1.1 Crear la carpeta raíz ##

```mkdir dev_environment
mkdir dev_environment

```

## 1.2 Estructura base en una única instrucción ##

```
mkdir -p dev_environment/{frontend/{public,src/{components,pages,styles}},backend/{app,config,tests},database/migrations,docs,scripts}
```
# 2. Inicialización de archivos #

## Frontend ##

```
cd dev_environment

ls

cd frontend

ls

cd public

touch index.html

cd ..

cd src

touch App.js 

cd styles

touch main.css

```

## Backend ## 

```
cd ..

ls

cd ..

ls

cd ..

ls

cd backend

cd app

touch server.js

cd ..

cd config 

touch config.json
```

##  General ##

```
cd ..

cd ..

ls 

touch README.md

cd 

ls

cd scripts

touch deploy.sh
```

# 3. Contenido #

##  Instalar nano ##

## Actualizar la lista de paquetes ##

```
apt update

```

## Instalacion nano ##

```
apt install nano -y

```
## Verificar version ##

```
nano --version
```

## Editar index.html , App.js , main.css con Nano ##

```
cd frontend 

nano index.html

<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <title>TechCore App</title>
    <link rel="stylesheet" href="main.css">
</head>
<body>
    <div id="root"></div>
    <script src="App.js"></script>
</body>
</html>

Ctrl + O

Enter

Ctrl + X


nano main.css

body {
    background-color: #f0f0f0;
    font-family: Arial, sans-serif;}

Ctrl + O

Enter

Ctrl + X

nano App.js

const root = document.getElementById('root');
root.innerHTML = '<h1>Entorno TechCore Listo</h1>';
console.log("Frontend cargado correctamente.");

Ctrl + O

Enter

Ctrl + X

```

# 4. Verificaciónn y Auditoria #

## Mostrar contenido ##

```
ls -R

o

tree dev_environment

```

## Mostrar archivos incluyendo ocultos ##

```
ls -la dev_environment
```

## Muestra el contenido de frontend/src/ ##

```
ls -l dev_environment/frontend/src/
```

# 5. Gestión de versiones #

## Crear Carpeta Backup ##

```
mkdir Backup
```

## Copiar frontend dentro Backup/ ##

```
cp -r frontend/ Backup/
```
## Copiar server.js como server_backup.js dentro Backup/ ##

```
cp server.js backup/server_backup.js
```

# 6. Reorganización del proyecto #

## Mueve main.css a frontend/public/ ##

```
mv main.css frontend/public/
```

## Renombra App.js a app.js ##
```
mv frontend/App.js frontend/app.js
```
## Mueve config.json a backend/app/## 
```
mv backend/config/config.json backend/app/
```
# 7. Permisos y Seguridad #

## deploy.sh → Ejecutable solo para el propietario ##

```
chmod 700 deploy.sh
```
## server.js → Lectura/escritura propietario, solo lectura grupo ##
```
chmod 640 server.js
```
## README.md → Solo lectura para todos ##

```
chmod 444 README.md
```

## Verificación de los permisos ##

```
ls -l deploy.sh server.js README.md
```

# 8. Simulación de error y recuperación #

## Elimina frontend/src/components/ ##

```
rm -r frontend/src/components/
```
## Recupérala desde backup/ ##

```
cp -r backup/frontend/src/components frontend/src/
```

# 9. Limpieza y Verificacion final #

##  Eliminar la carpeta temp/ ##

```
rm -r temp/

```
La carpeta no se puede borrar, por lo tanto da error: 
rm: cannot remove 'temp/': No such file or directory

## Eliminar server_backup.js ##
```
rm backup/server_backup.js
```

## Muestra la estructura completa del proyecto ##
```
tree dev_environment

```
## Muestra la ruta actual ##
```
pwd
```
## Muestra el historial de comandos ##

```
history
```

# Autor #

Mateo Garzon














