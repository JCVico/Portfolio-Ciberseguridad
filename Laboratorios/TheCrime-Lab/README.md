🧪 Laboratorio – CyberDefenders: The Crime Lab
Fecha de realización: 12/08/2025
Plataforma: CyberDefenders
Duración estimada: 4 horas
Nivel de dificultad: Media

🎯 Descripción
Análisis forense de un dispositivo móvil perteneciente a una víctima de homicidio. El objetivo fue extraer y correlacionar evidencias digitales para reconstruir eventos previos, identificando aplicaciones usadas, deuda contraída, acreedores, ubicaciones y comunicaciones relevantes.

🔍 Objetivos del análisis
Identificar la aplicación principal de trading usada por la víctima.

Determinar la deuda y la persona a la que se debía dinero.

Localizar la ubicación de la víctima en fechas clave y confirmar planes de viaje y encuentros.

🛠️ Herramientas utilizadas
ALEAPP v3.4.0

VirusTotal

Python 3.13.5

7-Zip

Entorno: Windows 10

✅ Resultados clave
Pregunta	Resultado
SHA256 de la aplicación de trading	4f168a772350f283a1c49e78c1548d7c2c6c05106d8b9feb825fdc3466e9df3c
Monto de la deuda	250000
Nombre de la persona a quien se debe dinero	Shady Wahab
Ubicación de la víctima el 20 de septiembre 2023	The Nile Ritz-Carlton
Destino de viaje planeado por la víctima	Las Vegas
Lugar del encuentro pactado vía Discord		The Mob Museum

🧪 Técnicas y filtros (si aplica)
Uso de ALEAPP para procesar la extracción completa del sistema de archivos Android.

Validación de hash SHA256 con VirusTotal para identificar aplicaciones sospechosas.

Búsqueda y análisis de registros de llamadas, mensajes y artefactos de ubicación.

Correlación de datos extraídos para responder preguntas específicas.

🧠 Reflexión personal
Este laboratorio me permitió combinar análisis forense móvil con herramientas automatizadas para obtener evidencias clave. Encontré desafíos en la extracción debido a la protección con contraseña del archivo ZIP, que resolví con 7-Zip. Validar el formato esperado en las respuestas fue crucial para evitar errores. En un entorno real, complementaría este análisis con otras herramientas y revisiones manuales para asegurar exhaustividad.

📁 Archivos
The Crime Lab.docx: Informe final del laboratorio
