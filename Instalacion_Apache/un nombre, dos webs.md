# Paso : Crear las carpetas y las páginas web
Creamos los directorios necesarios y los archivos HTML iniciales para la web pública y la intranet.

```sudo mkdir -p /var/www/smr/web /var/www/smr/intranet```

![image alt](https://github.com/abdulsyed631/Aplicaciones-Web/blob/a711a8b86f46334c7f1bd8d825ce3de20ff1824b/Instalacion_Apache/Imagenes/paso1%20creando%20archivos.png)

aqui ves que ha creado los dos archivos 

# Paso 1 Crear las carpetas y las páginas

Escribimos Bienvenidos a SMR como escribir? Con commando ``echo``

```
echo "<h1>Bienvenidos a SMR</h1>" | sudo tee /var/www/smr/web/index.html
echo "<h1>Intranet de SMR</h1>" | sudo tee /var/www/smr/intranet/intranet.html
```



# Paso 2 Crear el usuario de la intranet
```
sudo apt install apache2-utils -y
sudo htpasswd -c /etc/apache2/.htpasswd alumno
```

> [!NOTE]
> Os pedirá la contraseña dos veces. Ese usuario y esa contraseña serán los que pida la intranet.
yo he puesto ``1234``


![image alt](https://github.com/abdulsyed631/Aplicaciones-Web/blob/5e6e84aaf24a851ac6a87e2670a816c74d7b2ea1/Instalacion_Apache/Imagenes/passewd.png)
