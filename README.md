## 1. ¿Qué es YOLO?

YOLO (You Only Look Once) es un algoritmo de inteligencia artificial utilizado para detectar objetos en imágenes y videos en tiempo real. Puede identificar diferentes objetos y señalar su ubicación mediante cuadros delimitadores (bounding boxes).

Características principales:

Detecta objetos rápidamente.
Puede trabajar en tiempo real.
Identifica varios objetos en una misma imagen.
Indica la ubicación de cada objeto.
Es utilizado en cámaras de seguridad, vehículos autónomos, robótica y sistemas de visión artificial.
Tiene diferentes versiones, como YOLOv5, YOLOv8 y versiones posteriores.

¿Qué arquitectura tiene?

YOLO utiliza una arquitectura basada en redes neuronales convolucionales (CNN). Su funcionamiento analiza la imagen en una sola pasada para detectar los objetos, a diferencia de métodos que necesitan varias etapas para hacerlo.

## 2. Protocolo vs. Aplicación: TCP y UDP

La descarga del modelo utiliza TCP porque TCP garantiza que los datos lleguen completos y en el orden correcto. Si algún paquete se pierde, TCP puede solicitar que se vuelva a enviar.

La transmisión de video simulada utiliza UDP porque UDP es más rápido y tiene menor retraso. No necesita esperar a que los paquetes perdidos sean retransmitidos.

TCP	UDP
Mayor fiabilidad	Mayor velocidad
Comprueba la entrega	No garantiza la entrega
Reenvía paquetes perdidos	No reenvía automáticamente
Ideal para archivos	Ideal para video en tiempo real
## 3. Fiabilidad vs. Velocidad: tcp.analysis.retransmission

Si durante el análisis de descarga_tcp.pcap aparece tcp.analysis.retransmission, significa que un paquete TCP tuvo que ser enviado nuevamente, generalmente porque se perdió o no se recibió correctamente.

Este mecanismo es importante para descargar archivos porque garantiza que la información llegue completa y sin errores.

Sin embargo, en un video en vivo podría ser perjudicial porque esperar paquetes perdidos o retransmitirlos puede producir retrasos, pausas o congelamientos. En video en vivo normalmente es preferible perder algunos datos antes que detener la transmisión para recuperarlos.

Nota: si en tu captura no aparece tcp.analysis.retransmission, puedes escribir: “No se observaron retransmisiones TCP durante el análisis de la captura.”# Ejercicio-en-clase
## 4. Identificando el origen con ip.src e ip.dst

Para identificar el servidor que entregó el modelo, primero se puede observar en Wireshark las direcciones IP que aparecen durante la descarga.

Por ejemplo, si identificamos que el servidor tiene la IP X.X.X.X, podemos utilizar:

ip.dst == X.X.X.X

Esto muestra los paquetes que van hacia ese servidor.

También podemos utilizar:

ip.src == X.X.X.X

Esto muestra los paquetes que vienen desde ese servidor.

Para observar toda la comunicación entre nuestro equipo y ese servidor, podemos usar:

ip.addr == X.X.X.X
