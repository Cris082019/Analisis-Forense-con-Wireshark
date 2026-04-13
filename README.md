<img width="831" height="460" alt="image" src="https://github.com/user-attachments/assets/54b6f069-21cc-4806-9a7d-0a498fcc7bcd" />

*PASO 1*<br>
Inicialmente se crea cuenta en Google Colab, para poder ejecutar los comandos que se encuentran en la imagen, se adjunta evidencia del aplicativo ya mencionado
<img width="831" height="460" alt="image" src="https://github.com/user-attachments/assets/a74d4b97-1d13-4a35-bb0d-ea3849e01af7" /><br>
Se ejecutan los comandos como se requiere, y la siguiente imagen es el resulatado de esto
<img width="831" height="460" alt="image" src="https://github.com/user-attachments/assets/d40adde7-39ca-45e7-91a0-ab19e8cf9a1b" />





<img width="831" height="460" alt="image" src="https://github.com/user-attachments/assets/b016ca68-bd3d-45cf-993c-c1fd6b3a7196" />
<img width="831" height="460" alt="image" src="https://github.com/user-attachments/assets/bb09db28-3beb-4dd9-ab35-bf7a4f37ffad" /><br>
Se deben ejecutar ahora los siguientes comandos, y esto es el resultado que arroja
<img width="831" height="460" alt="image" src="https://github.com/user-attachments/assets/fd7663bd-1f20-42e3-a66a-c6c1173bf9e3" /><br><br>

Para la fase dos, se ejecutan los comandos, sin embargo, en el transcurso de ellos se descarga el archivo, pero no se obtiene paquetes, esto se evidencia en las siguientes imagenes que se van a compartir a continuación:
<img width="831" height="460" alt="image" src="https://github.com/user-attachments/assets/d9e04dd5-08ad-4d94-9d08-24218867dd36" />
<img width="831" height="460" alt="image" src="https://github.com/user-attachments/assets/583a05ea-ace9-4888-a27f-5d6f69d9dc27" />
<img width="831" height="460" alt="image" src="https://github.com/user-attachments/assets/0d6822e8-063b-46e1-b84e-6f5308d88ab4" /><br><br>
Estos son los resultados, adicional para que funcionara YOLO, se realiza un script Java para que muestre imagen.
<img width="831" height="460" alt="image" src="https://github.com/user-attachments/assets/5ef639f3-26e8-4526-999d-b90abe006b2f" />
<img width="831" height="460" alt="image" src="https://github.com/user-attachments/assets/db39a359-fed0-4953-b356-a6792e11cd9b" />
<img width="831" height="460" alt="image" src="https://github.com/user-attachments/assets/7e8c7fea-2849-4a22-9a75-d20ebdd6728b" />
<img width="831" height="460" alt="image" src="https://github.com/user-attachments/assets/e02e6327-fae5-4f9c-97a5-77945a8ba3ec" /><br><br>

Se decide ejecutar el siguiente comando con el fin de saber en que interface se encuentra la imagen o video para que pueda descargar el archivo con los paquetes, sin embargo, se toma en las primeras imágenes con eth0, luego se hace con lo(Loopback) y por último se procede con la IP, pero ningún resultado me muestra los paquetes como se muestra a continuación.
<img width="831" height="460" alt="image" src="https://github.com/user-attachments/assets/5c921fe3-ff81-4aa8-abcf-41a56e40a7b7" />
<img width="831" height="460" alt="image" src="https://github.com/user-attachments/assets/b2a43dfb-5279-4ace-a30a-ef3d5792bbdb" /><br><br>

Ahora se va a realizar el analisis con Wireshark, para este caso se va a ver el primer paso TCP:
<img width="831" height="460" alt="image" src="https://github.com/user-attachments/assets/1daab1c8-aab8-4f0a-9b5a-c8d9cd49ef06" />
<img width="831" height="460" alt="image" src="https://github.com/user-attachments/assets/371100d2-6a91-441c-aea7-67a53d44cd48" />
<img width="831" height="460" alt="image" src="https://github.com/user-attachments/assets/8ed5facf-aed4-4458-8137-90bce9ade735" />
<img width="831" height="460" alt="image" src="https://github.com/user-attachments/assets/6ffe50f0-8b45-4847-b07e-43cd0f3aa87c" />
<img width="831" height="460" alt="image" src="https://github.com/user-attachments/assets/31ff3e47-dafa-4da8-814a-188a86a2e2b7" /><br><br>

Por útimo, se van a resolver las preguntas que se dejan al final, con el fin de comprender el funcionamiento de YOLO y el analisis de Wireshark
<img width="831" height="460" alt="image" src="https://github.com/user-attachments/assets/b87159ee-cce1-4190-91a9-ef31cd1a4c24" />

***1. ¿Qué es YOLO?, ¿Cuáles son sus características principales? y ¿Qué arquitectura tiene?***<br>
YOLO (You Only Look Once) es un modelo de visión por computadora diseñado para la detección de objetos en tiempo real.<br><br>
*Características principales:*<br>
*🔴Velocidad:* Es extremadamente rápido al procesar imágenes completas en una sola pasada de red, lo que permite su uso en video en tiempo real.<br>
🔴*Precisión:* A pesar de su rapidez, mantiene una alta precisión en la localización y clasificación de objetos.<br>
🔴*Eficiencia:* Existen versiones como YOLOv8 Nano (yolov8n.pt) optimizadas para dispositivos con recursos limitados.<br>
➖*Arquitectura:* Utiliza una red neuronal convolucional (CNN) que divide la imagen en una cuadrícula. Cada celda de la cuadrícula es responsable de predecir cajas delimitadoras (bounding boxes) y las probabilidades de clase simultáneamente.<br><br>

***2. Protocolo vs. Aplicación: ¿Por qué la descarga usa TCP y la transmisión usa UDP?*** <br>
La elección del protocolo depende de la prioridad de la tarea:<br>
🟢*Descarga del Modelo (TCP):* Se utiliza TCP porque es un protocolo orientado a conexión y fiable. Para que el archivo del modelo (.pt) funcione, cada bit debe llegar intacto; un error de un solo byte corrompería el "cerebro" de la IA y no cargaría.<br>
🟢*Transmisión de Video (UDP):* Se utiliza UDP para minimizar la latencia. En el video en tiempo real, es preferible perder un paquete (un pequeño cuadro o pixelado) y continuar con el siguiente frame que detener el video esperando una retransmisión.<br><br>

***3. Fiabilidad vs. Velocidad: Análisis de Retransmisiones*** <br>
🔵**tcp.analysis.retransmission:** Si aparece este filtro en Wireshark, significa que un paquete se perdió en la red o llegó dañado, y el receptor solicitó que se enviara de nuevo.<br>
🔵**Crucial para archivos:** Sin este mecanismo, las descargas de archivos pesados fallarían constantemente ante cualquier parpadeo del Wi-Fi.<br>
🔵**Perjudicial para video:** En un video en vivo, recibir un paquete "viejo" que se perdió hace 2 segundos causaría saltos o congelamientos molestos; es mejor ignorar la pérdida y mostrar lo que está pasando ahora.<br><br>
