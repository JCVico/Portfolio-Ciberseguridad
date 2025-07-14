# 🧪 Laboratorio – CyberDefenders: Lespion

**Fecha de realización:** 14/07/2025  
**Plataforma:** CyberDefenders  
**Duración estimada:** 1,5 horas  
**Nivel de dificultad:** Media

---

## 🎯 Descripción

El equipo de seguridad recibió varios artefactos relacionados con un posible caso de fuga de información y uso de herramientas maliciosas 
por parte de un empleado. Mediante técnicas OSINT y análisis de fuentes abiertas (imágenes, redes sociales, GitHub), se investigó al actor
 sospechoso y se recopilaron indicadores clave.

---

## 🔍 Objetivos del análisis

- Aplicar técnicas OSINT para rastrear perfiles y comportamientos sospechosos.
- Extraer credenciales y claves desde código público.
- Realizar geolocalización a partir de imágenes públicas.
- Analizar repositorios GitHub para identificar herramientas maliciosas.

---

## 🛠️ Herramientas utilizadas

- [CyberChef](https://gchq.github.io/CyberChef/)
- Google Search / Reverse Image
- GitHub
- Instagram / LinkedIn
- EXIF Viewer (opcional)
- SO anfitrión: Navegador web y herramientas online

---

## ✅ Resultados clave

| Pregunta                                     | Resultado                                      |
|---------------------------------------------|-----------------------------------------------|
| **Usuario sospechoso**                      | `EMarseille99`                                 |
| **Clave API encontrada**                    | `aJFRaLHjMXvYZgLPwiJkroYLGRkNBW`               |
| **Contraseña decodificada (Base64)**        | `PicassoBaguette99`                            |
| **Herramienta de minado usada**             | `xmrig`                                        |
| **Ubicación de oficina (foto office.jpg)**  | Birmingham, Reino Unido                        |
| **Ubicación webcam (Webcam.png)**           | Indiana, Estados Unidos                        |
| **Viaje reciente (Instagram)**              | SkyPark, Singapur                              |
| **Origen familiar (Instagram)**             | Dubái, Emiratos Árabes                         |

---

## 🧪 Técnicas y filtros

- Decodificación de cadenas en Base64 con CyberChef.
- Búsqueda inversa de imágenes con Google.
- Identificación de claves API en código fuente.
- Técnicas MITRE ATT&CK observadas:
  - `T1087` – Account Discovery  
  - `T1589` – Gather Victim Identity Information  
  - `T1040` – Network Sniffing  
  - `T1204` – User Execution

---

## 🧠 Reflexión personal

Este laboratorio me permitió consolidar el uso de técnicas OSINT para rastrear actores maliciosos a través de artefactos públicos. 
Fue interesante ver cómo una simple imagen o repositorio puede derivar en múltiples hallazgos críticos. La dificultad principal fue la localización precisa 
de lugares mediante imágenes. En un entorno real, complementaría este análisis con verificación de logs, red y endpoints relacionados.

---

## 📁 Archivos

- [`Lespion Lab.docx`](./Lespion%20Lab.docx): Informe final del laboratorio

> 🔐 Las evidencias originales del laboratorio no se incluyen por respeto a los términos de uso de CyberDefenders.
