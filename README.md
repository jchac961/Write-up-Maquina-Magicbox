<img width="655" height="274" alt="Captura de pantalla 2026-06-03 012801" src="https://github.com/user-attachments/assets/61e40a20-ab82-41c3-a331-7b4880771302" />


# Write-up-Maquina-Magicbox

Maquina de la plataforma www.whoami-labs.com

Iniciamos la maquina vulnerable

<img width="1920" height="1140" alt="Captura de pantalla 2026-06-03 005455" src="https://github.com/user-attachments/assets/63729281-dfc0-44c3-a45a-3bb11ed5552c" />

# Reconocimiento

Una vez iniciada la maquina vulnerable realice un escaneo de puertos utilizando la herramienta nmap

<img width="1920" height="1140" alt="Captura de pantalla 2026-06-03 005513" src="https://github.com/user-attachments/assets/c42ca977-d664-4bb5-8c12-5d1a03cbe042" />

En vista de que solo tenia el puertto #80 abierto procedi inmediatamenta a verificar el contenido de este server en un navegador web

<img width="1920" height="1140" alt="Captura de pantalla 2026-06-03 005525" src="https://github.com/user-attachments/assets/7e23ff39-0288-4c88-836e-36ef33f726be" />

Dentro de las paginas encontradas tenemos un dashboard que nos permite subir imagenes gif,jpg o png

<img width="1920" height="1140" alt="Captura de pantalla 2026-06-03 005534" src="https://github.com/user-attachments/assets/faee8472-665e-4011-993b-bf50478770cc" />

Hice un fuzzing utilizando la herramienta feroxbuster, donde pudimos observar que habia un directorio llamado uploads que era donde se guardaban las inagenes que se subian

<img width="1920" height="1140" alt="Captura de pantalla 2026-06-03 005914" src="https://github.com/user-attachments/assets/7391a239-4532-41f8-acec-20538fc247e8" />

Verificamos el user.txt el cual contenia una flag que me supuse era la de usuario pero en este caso no quise utilizarla aun

<img width="1920" height="1140" alt="Captura de pantalla 2026-06-03 005925" src="https://github.com/user-attachments/assets/b8b90d95-f5c2-4695-be32-06fb63f4fe03" />

Ya que vimos que solo podiamos utilizar archivos gif procedimos a crear uno llamado imagen2.phtml en un nano, la cual contendria el codigo php que me permitiria obtener la reverse shell, y lugo la convertimos a imagen2.gif para que lo permitiera la pagina

<img width="1920" height="1140" alt="Captura de pantalla 2026-06-03 010113" src="https://github.com/user-attachments/assets/9e2447e7-f9e7-45ee-9e54-e5609eeb37cd" />

Procedimos a subir la imagen pero tambien pusimos la herramienta burpsuite a interceptar el trafico para poder obtener acceso

<img width="1920" height="1140" alt="Captura de pantalla 2026-06-03 010200" src="https://github.com/user-attachments/assets/2d840311-1275-49bb-93fc-5d5fa0b9126d" />

<img width="1920" height="1140" alt="Captura de pantalla 2026-06-03 010212" src="https://github.com/user-attachments/assets/d990d720-a9c6-40c8-9f3f-1e0c2c73662a" />

La pasamos al repeater

<img width="1920" height="1140" alt="Captura de pantalla 2026-06-03 010221" src="https://github.com/user-attachments/assets/f71ee8f6-5c5d-41e5-bf0f-bdaa01bdc386" />

Cambiamos la extension del archivo, y cambiamos el numero que efectivamente la hace pasar por el archivo gif

<img width="1920" height="1140" alt="Captura de pantalla 2026-06-03 012142" src="https://github.com/user-attachments/assets/08fab0cf-873d-4754-bab4-d0902291dcba" />

# EXPLOTACIÓN

Desactivamos el burpsuite y procedimos a buscar la carpeta uploads y encontramos el archivo que acababamos de subir

<img width="1920" height="1140" alt="Captura de pantalla 2026-06-03 012236" src="https://github.com/user-attachments/assets/7fbcb261-8250-4bbd-a0ac-d7f52f989893" />

Ya teniamos nuestro kali en modo escucha

<img width="1920" height="1140" alt="Captura de pantalla 2026-06-03 010315" src="https://github.com/user-attachments/assets/bf2e77c8-95c3-40ad-b3d6-3ce79dbf9e5a" />

Abrimos el archivo y obtuvimos acceso a la maquina

<img width="1920" height="1140" alt="Captura de pantalla 2026-06-03 012247" src="https://github.com/user-attachments/assets/69a7c127-7eb8-42bf-98cc-63e6da3128bc" />

Buscamos la flag de usuario que resulto ser la misma que habiamos visto anteriormente en el archivo user.txt

<img width="1920" height="1140" alt="Captura de pantalla 2026-06-03 012333" src="https://github.com/user-attachments/assets/36bb5394-a08c-4bef-8877-4231fc6f9216" />

# ESCALADA DE PRIVILEGIOS

Buscamos sudo -l para ver si este usuario podia ejecutar algun archivo como sudo pero no, asi que procedimos a buscar los binarios y encontramos el binario find, el cual utilizamos y obtuvimos el acceso como root

<img width="1920" height="1140" alt="Captura de pantalla 2026-06-03 012613" src="https://github.com/user-attachments/assets/e41f7c92-0967-4fd7-9bd1-f14c3e50ccc9" />

# RESULTADOS

Buscamos la flag

<img width="1920" height="1140" alt="Captura de pantalla 2026-06-03 012635" src="https://github.com/user-attachments/assets/4c2091c0-6487-4f21-9b69-861f6e88f4ac" />

lISTO

<img width="1920" height="1140" alt="Captura de pantalla 2026-06-03 012648" src="https://github.com/user-attachments/assets/fdff67f1-ec58-40ea-b142-64be97de0acc" />

👌

<img width="2688" height="1596" alt="Imagen Powned JCpty1391" src="https://github.com/user-attachments/assets/5db36d25-db31-43e0-aa4c-9694ce77e3cb" />
