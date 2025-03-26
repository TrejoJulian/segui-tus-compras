# Instalacion del proyecto

### Prerequisitos

Si se esta uilizando Windows se necesita instalar [WSL](https://learn.microsoft.com/es-es/windows/wsl/install), y tambien [Docker Desktop](https://www.docker.com/products/docker-desktop/).

Tildar las siguientes opciones en Docker Desktop

![image](https://github.com/user-attachments/assets/112d87de-1649-4870-b1ac-62ea57ad1146)

![image](https://github.com/user-attachments/assets/f9454160-0f1b-4fb6-98be-a1526ad64788)


### Pasos

- Si estamos utilizando WSL, ir al subsitema linux que tengamos instalado, a la home por ejemplo.
- Clonar el repo
- cd segui-tus-compras
- Crear una copia del environment: `cp .env.example .env`
- modificar el .env quitando los # de todos los campos que comiencen con `DB`, y cambiar el username y password de DB por `sail` y `password` respectivamente.
- Correr el siguiente comando: 
```
docker run --rm \
    -u "$(id -u):$(id -g)" \
    -v "$(pwd):/var/www/html" \
    -w /var/www/html \
    laravelsail/php82-composer:latest \
    composer install --ignore-platform-reqs
```

- Correr el comando `./vendor/bin/sail up -d`
- Correr el comando `./vendor/bin/sail artisan key:generate` para crear la key de la aplicacion
- Correr el comando `./vendor/bin/sail npm i` para instalar las dependencias del frontend
- Correr el comando `./vendor/bin/sail artisan migrate` para ejecutar las migraciones
  - Ya podemos acceder al proyecto en `localhost:80`


### Como levantar el proyecto

Para levantar el proyecto en cualquier momento, una vez instalado, simplemente hay que ir a la carpeta del proyecto en una consola y ejecutar `./vendor/bin/sail up -d`. El proyecto estara levantado en `localhost:80`
