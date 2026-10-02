# Practica-Wifi-Segura
Introducción El propósito de este informe es evaluar los riesgos de seguridad asociados a la navegación web mediante protocolos en texto plano (sin cifrar) cuando un usuario se conecta a redes Wi-Fi públicas o abiertas. A través de un ejercicio práctico de inspección de tráfico con las Herramientas de Desarrollador (DevTools) y captura de paquetes, se analiza cómo la falta de cifrado expone la información personal y técnica del usuario ante posibles atacantes locales.

Sitio Web Analizado Dominio: http://neverssl.com 
Protocolo:HTTP (HyperText Transfer Protocol)
Puerto utilizado: Puerto 80  
Estado de Cifrado:Inseguro / Texto Plano (Plaintext) 
El sitio \`neverssl.com\` es un servicio diseñado intencionalmente para no implementar TLS/SSL, manteniendo la comunicación en texto abierto.
Evidencia Observada (Análisis de Solicitud) Al inspeccionar la pestaña Network(Red) en las Herramientas de Desarrollador (F12) tras recargar la página, se identificaron los siguientes elementos visibles en la solicitud raíz.
![Uploading image.png…](https://github.com/melgarejomartin2006-create/practica-wifi-segura/blob/d9b10b73a43236d04f2ad31e9f0f20ff05492326/Wifi%20seguro1.jpeg)
<img width="698" height="645" alt="image" src="https://github.com/user-attachments/assets/982733a7-5d0d-4f0f-922f-825afe587c91" />
1.URL Solicitada:http://neverssl.com/ 

2. Método HTTP:GET (solicitud de lectura de recursos)
3. Host:neverssl.com (o subdominios asignados por la CDN)
4. Protocolo:HTTP/1.1
5. Código de Respuesta:200 OK 
6. Encabezados (Headers) expuestos:
7. User-Agent: Revela el navegador exacto, la versión y el sistema operativo del usuario.
8. Accept-Language: Expone los idiomas y la localización preferida del usuario.
9. Host: Confirma el nombre del servidor de destino. Payload / HTML: Las 131 líneas de código fuente HTML y el texto del sitio son totalmente legibles.

Riesgos Encontrados en Redes Wi-Fi Públicas

1. Navegar en un sitio web HTTP desde una red Wi-Fi compartida presenta graves amenazas debido a que los datos viajan "en el aire" sin ninguna protección
2. Intercepción de Datos (Sniffing / Eavesdropping):Cualquier usuario en la misma red pública puede usar analizadores de paquetes (como Wireshark) para capturar el tráfico y leer credenciales, cookies o formularios en texto plano
3. Falta de Confidencialidad e Integridad:Los mensajes pueden ser interceptados y modificados en tránsito mediante ataques de Intermediario (Man-in-the-Middle - MitM) o inyección de código malicioso sin que el usuario lo note
4. Redes Gemelas Malignas (Evil Twins): Un atacante puede montar un punto de acceso falso con el mismo nombre de la cafetería o aeropuerto para capturar todo el tráfico no cifrado del usuario.

Simulación de Escenario con una VPN Si el usuario estuviera conectado a una VPN (Red Privada Virtual), el escenario cambiaría de la siguiente manera
Túnel Cifrado:La VPN encapsula todo el tráfico emitido por el dispositivo dentro de un túnel cifrado (ej. algoritmos AES) antes de salir a la red pública.

Invisibilidad Local: Aunque el usuario acceda a una página HTTP, un atacante capturando paquetes en la Wi-Fi pública solo verá bloques de caracteres aleatorios e ininteligibles Application Data dirigiéndose al servidor VPN.

Ocultamiento de IP y Ubicación:La dirección IP real del usuario queda oculta y es reemplazada por la dirección IP del servidor VPN, protegiendo su identidad digital.
