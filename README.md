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
