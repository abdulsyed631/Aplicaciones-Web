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


# Paso 3 · 
Decirle a Apache que escuche en el puerto 9999
```
sudo nano /etc/apache2/ports.conf
```
```
Listen 80
Listen 9999
```
![image alt](https://github.com/abdulsyed631/Aplicaciones-Web/blob/23816c685b510da61e0dceeb809005f3c46aa0a9/Instalacion_Apache/Imagenes/listen%209999.png)


# Paso 4 · Crear el virtualhost
```
sudo nano /etc/apache2/sites-available/smr.conf
```

antes

<img width="719" height="95" alt="image" src="https://github.com/user-attachments/assets/a4d2c617-d905-4eb9-9964-8b3a7e3359a1" />

despues

<img width="683" height="61" alt="image" src="https://github.com/user-attachments/assets/5c58f8ed-956f-4fb1-8cea-3b2af20a3d56" />

cuando abres ```sudo nano /etc/apache2/sites-available/smr.conf```
pegas esto para crear virtual host
![image alt](https://github.com/abdulsyed631/Aplicaciones-Web/blob/34e4bf2c19130423dfd1b7a647e2dc5747d17467/Instalacion_Apache/Imagenes/creando%20virtual%20host.png)


> [!IMPORTANT]
>  ServerName: el nombre de la web (igual en los dos bloques).
>
>  DocumentRoot: la carpeta donde están las páginas de cada web.
>
>  DirectoryIndex: la página principal de la intranet, ya que no es index.html.
>
>  El bloque Directory es lo que pide usuario y contraseña (ya lo conocéis de la práctica anterior).


Paso 5 · Activar el sitio y reiniciar Apache

```
sudo a2ensite smr.conf
sudo a2dissite 000-default.conf
sudo apachectl configtest
sudo systemctl restart apache2
```

<img width="1273" height="276" alt="image" src="https://github.com/user-attachments/assets/5985f2cc-ff09-49c0-8d94-df91be92e526" />


# PASO 6 Paso 6 · Comprobar que funciona


![image alt](https://github.com/abdulsyed631/Aplicaciones-Web/blob/c851fc708c6e49575b9b6c081afdaff2958f30b8/Instalacion_Apache/Imagenes/comprobamos%20sitioweb%2080.png)

y en el puerto :9999 me pide usario y la contresena 

![image alt](https://github.com/abdulsyed631/Aplicaciones-Web/blob/b62fbd2511c593bc924aedfbf2e7bfa09f885a2f/Instalacion_Apache/Imagenes/comprobacion%20sitio%20web%209999.png)


> [!WARNING]
>Me esta donde problemas al intrar con el nombre ``http://smr.com``
> <img height="260" alt="image" src="https://github.com/user-attachments/assets/1061dc63-fc08-4a13-ab16-cbaac2d28ff5" />
><img  width="500" alt="image" src="https://github.com/user-attachments/assets/6c6c82a5-210e-420c-85fe-6aab0f49a5e3" />

<!--width="1281" height="660"
 width="1277" height="829" -->


> [!TIP]
>Nota de resolución de problemas:
>Inicialmente la web no cargaba desde la máquina cliente porque estaba modificando el archivo >/etc/hosts únicamente en el propio servidor Ubuntu. El error se solucionó al comprender que >la asignación del dominio [www.smr.com](https://www.smr.com) a la IP local debía hacerse en >el archivo hosts del cliente (la máquina desde la que se navega) para que el navegador >pudiera resolver el nombre correctamente


# Ahora si quieres buscar desde windows se hace asi

Paso 1 
Abres cmd y ejuctas como administrador 
pegas este comando
```
notepad C:\Windows\System32\drivers\etc\hosts
```
<img width="972" height="508" alt="image" src="https://github.com/user-attachments/assets/099f6849-206f-4834-b2ed-024a1ec2b63d" />


paso 2 se abre un note pad pegas tu ip y el domainio que queires poner


<img height="450" alt="image" src="https://github.com/user-attachments/assets/20553cdc-866d-47af-8e95-2a404650cf61" />

Paso 3 comprobacion

<img width="2559" height="1439" alt="image" src="https://github.com/user-attachments/assets/0cb473c4-fcfb-435e-8229-580b7bb08a62" />



Ahora funciona desde windows tmb



