# SISTEMA DE GESTION DE MARCACIONES - SGM


## Tabla de Contenido
1. [Descripcion](#descripcion)
2. [Tecnologias](#tecnologias)
3. [Configuracion Entorno](#configuracion-entorno)
4. [Clonar Proyecto](#importar-proyecto)
5. [Colaboradores](#colaboradores)
6. [Preguntas](#faqs)
### Descripcion
Entorno de Desarrollo del Proyecto de Sistema de Marcacion de Funcionarios.
### Screenshot
![Image text](https://www.united-internet.de/fileadmin/user_upload/Brands/Downloads/Logo_IONOS_by.jpg)
***
## Tecnologias
Listado de Tecnologias usados en el proyecto:
* [Postgresql](https://www.postgresql.org/download/): Version 16.4 
* [PHP](https://www.php.net/downloads): Version 8.3.6
* [Ngix](https://nginx.org/en/download.html): Version 1234
* [Composer](https://getcomposer.org/download/): Version 2.7.7
* [Symfony](https://symfony.com/download): Version 7.1.3
***
## Configuracion Entorno
#### Postgresql
-Creacion de usuario ```user_sgm``` para la Base de Datos ```sgm```, esta configuracion servira como un estandar en las conexiones al motor de base de datos.
```
CREATE USER user_sgm WITH PASSWORD '.us3r*r00t..';

CREATE DATABASE sgm OWNER user_sgm; 
```
***
#### Servidor Nginx
-Configuracion de Host Virtual 

Cambia al directorio donde se encuentran las configuraciones de sitios de Nginx. ```cd /etc/nginx/sites-available/ ```
Abre un editor de texto para editar el archivo de configuración del host virtual de Symfony. ```vi etc/nginx/sites-available/nombre_dominio``` 
Agregar el contenido al archivo dominio, que configura un host virtual para servir el proyecto Laravel.
```
server {
  listen 81;
  listen [::]:81;
  server_name example.com;
  root /var/www/html/example.com/public;
 
  add_header X-Frame-Options "SAMEORIGIN";
  add_header X-Content-Type-Options "nosniff";
 
  index index.php;
 
  charset utf-8;
 
   location / {
      try_files $uri $uri/ /index.php?$query_string;
   }
 
   location = /favicon.ico { access_log off; log_not_found off; }
   location = /robots.txt  { access_log off; log_not_found off; }
 
  error_page 404 /index.php;
 
   location ~ \.php$ {
      fastcgi_pass unix:/var/run/php/php8.3-fpm.sock;
      fastcgi_param SCRIPT_FILENAME $realpath_root$fastcgi_script_name;
      include fastcgi_params;
      fastcgi_hide_header X-Powered-By;
   }
 
   location ~ /\.(?!well-known).* {
      deny all;
   }
}
```
Habilita el archivo creado para el directorio ```/etc/nginx/sites-enabled``` 
```
sudo ln -s /etc/nginx/sites-available/your_domain /etc/nginx/sites-enabled/
```

Verifica la sintaxis de los archivos de configuración de Nginx para asegurar que no haya errores. ```sudo nginx -t```

Recarga Nginx para aplicar los cambios realizados en su configuración. ```sudo systemctl restart nginx```
***
```
$ git clone https://example.com
$ cd ../path/to/the/file
$ npm install
$ npm start
```
***
Side information: To use the application in a special environment use ```lorem ipsum``` to start
## Collaboration
***
Give instructions on how to collaborate with your project.
> Maybe you want to write a quote in this part. 
> It should go over several rows?
> This is how you do it.
## FAQs
***
A list of frequently asked questions
1. **This is a question in bold**
Answer of the first question with _italic words_. 
2. __Second question in bold__ 
To answer this question we use an unordered list:
* First point
* Second Point
* Third point
3. **Third question in bold**
Answer of the third question with *italic words*.
4. **Fourth question in bold**
| Headline 1 in the tablehead | Headline 2 in the tablehead | Headline 3 in the tablehead |
|:--------------|:-------------:|--------------:|
| text-align left | text-align center | text-align right |
