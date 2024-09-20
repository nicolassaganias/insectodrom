# Insectodrom
Raspberry-pi cam for monitoring nature. Camera and Microphone will stream to youtube.

## Descripción
Contruiremos un sistema de monitorización (audio y video) de la biodiversidad DIY con raspberry pi y energía solar que nos permitirá observar la vida de los insectos a través de un streaming en directo por un canal de youtube.
Insectodrom es un proyecto multidisciplinar que, desde la práctica concreta de construir hostales de insectos para ayudar a su reproducción y conservación, intenta poner foco en cuestiones como la ecología, el ecofemismo, la colaboración y la simbiosis vs el modelo capitalista, de extracción y competitividad.
_En este apartado nos centraremos en una parte de un trabajo colectivo y más amplio llamado Insectodrom._   
_Work in process. Todavía no se encuentra implementada la alimentación por energía solar_

## Materiales
- Raspberry pi 4 16GB https://www.raspberrypi.com/products/raspberry-pi-4-model-b/. 
- Camera https://www.raspberrypi.com/products/camera-module-v2/. 
- Microphone https://thepihut.com/products/mini-usb-microphone

## Instalación
1. Descargar la imagen: https://mega.nz/file/DNBEQLZL#KLV7qg4G9lPoobz-tsR3XDQdrVh1X6GpSQKMIIuVwK0 
2. Quemar la imagen en una sd de al menos 16BG. Quemar sd con RaspberryPi Imager https://www.raspberrypi.com/documentation/computers/getting-started.html#installing-images-on-mac-os. 
3. Insertar la microSD en la raspberry pi.
4. Conectar la cámara: https://projects.raspberrypi.org/en/projects/getting-started-with-picamera.
5. Configurar red WIFI e ingresar clave de stream de youtube.
- En este link pueden ver una guía detallada de como obtener la clave de stream de youtube: https://projects.raspberrypi.org/en/projects/infrared-bird-box/9

### Para configurar la clave de wifi y configurar la clave del stream hay 2 opciones:
1. Conectar mouse, teclado y monitor a la raspberry pi
2. Conectarse vía real vnc con otro ordenador. guía para real vnc: https://www.realvnc.com/es/raspberrypi/

## Uso

El código que hace todas las acciones para que el streaming suceda es el siguiente: 

`raspivid -o - -t 0 -w 1280 -h 720 -fps 25 -b 4000000 -g 50 | ffmpeg -re -ar 44100 -ac 2 -acodec pcm_s16le -f s16le -ac 2 -i /dev/zero -f h264 -i - -vcodec copy -acodec aac -ab 128k -g 50 -strict experimental -f flv rtmp://a.rtmp.youtube.com/live2/<key goes here>
`
en <key goes here> deberás escribir la clave de stream que conseguimos antes.

En este link veremos una explicación detallada de cada parte del código: https://projects.raspberrypi.org/en/projects/infrared-bird-box/10

## Autorxs y Agradecimientos
Nicolás Saganías, Tsune Martinez Zaragoza, Rachel Demetz, Marta Sureda, Ingrid Guardiola, Bolit Centre d'Art Contemporani, Iraia, Emily, Si els mobles parlassin

## Open-source
Proyecto open-source.

## Estado del proyecto
Work in process.

