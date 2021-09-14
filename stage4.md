# Paso a producción: servidor

Transferir tu sevidor de ExpressJS local a producción supone _desplegar_ los archivos que la componen a un servidor externo (tu aplicación de Heroku), permitiendo así que las respuestas que ahora se emiten desde `http://localhost:3000` pasen a realizarse desde `https://donuts-planet.herokuapp.com`.
       
## Variables de entorno remoto

Debido a que el archivo `.env` no será desplegado, es necesario habilitar las variables de entorno en tu aplicación de Heroku.

Para ello, tenemos 2 opciones: 

1 - mediante la terminal al directorio raíz de tu servidor y asegúrate de que está enlazado al Git de servidor mediante `heroku apps:info`. Declara entonces cada una de las variables de entorno de tu archivo `.env` con el comando `heroku config:set NOMBREVARIABLE=”VALORVARIABLE” --app nombreApp`. Ejemplo:

       heroku config:set CLOUDINARY_NAME="german-cloud" --app donuts-planet
  
No olvides entrecomillar el valor de cada variable. Puedes consultar el valor de cualquier variable de entorno con el comando `heroku config:get NOMBREVARIABLE` 

2 - Nos diriijimos la interfaz de heroku en https://id.heroku.com/login 
       - Logueamos y seleccionamos el proyecto
       - Pestaña Setting y presionar Reveal config Vars
  <img src="https://res.cloudinary.com/dnpvaaivi/image/upload/v1631632251/Captura_de_pantalla_2021-09-14_a_las_17.02.00_p0ryy8.png" width="400"/><br/><br/>
  <img src="https://res.cloudinary.com/dnpvaaivi/image/upload/v1631632258/Captura_de_pantalla_2021-09-14_a_las_17.04.10_lafnts.png" width="400"/><br/><br/>


## Paso a producción

Transferir los archivos a la aplicación de Heroku hará accesible tu servidor desde tu URL de Heroku.

1. Accede mediante la terminal a la raíz de tu servidor, donde se encuentra el archivo `package.json`.
2. Revisa que dispones de un archivo `.gitignore` donde se ignoran tanto `/node_modules` como `.env`.
3. Procede a la subida:
       
       git push heroku master

4. Una vez finalizado, comprueba la ausencia de errores en los logs mediante el comando `heroku logs --tail`.
5. Abre tu aplicación en el navegador mediante `heroku open`, o tecleando la URL de la misma. Podrás comprobar que funciona con normalidad, ahora en remoto.

## Interfaz de usuario de Heroku

Puedes acceder a [tu cuenta de Heroku](https://dashboard.heroku.com/apps) mediante el navegador para comprobar detalles de tus aplicaciones: commits (pestaña *Activity*), variables de entorno (pestaña *Settings*), o incluso trabajar con la consola de Heroku en la esquina superior derecha *More => Console*.
