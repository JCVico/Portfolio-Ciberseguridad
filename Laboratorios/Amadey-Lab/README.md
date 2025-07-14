# 🧪 Laboratorio – CyberDefenders: Amadey

**Fecha de realización:** 14/07/2025  
**Plataforma:** CyberDefenders  
**Duración estimada:** 2 horas  
**Nivel de dificultad:** Media

---

## 🎯 Descripción

El equipo de seguridad ha recibido una imagen de memoria RAM de un sistema Windows 7 sospechoso de estar comprometido por malware. 
La misión del analista es investigar indicios de infección y determinar vectores de persistencia, comunicación externa y malware ejecutado.

---

## 🔍 Objetivos del análisis

- Analizar una imagen de memoria comprometida.
- Identificar procesos maliciosos.
- Detectar persistencia y actividad de malware.
- Reconocer tráfico de comando y control (C2).
- Aplicar técnicas de análisis forense de memoria con Volatility.

---

## 🛠️ Herramientas utilizadas

- [Volatility 3](https://www.volatilityfoundation.org/)
- Strings
- grep / awk
- SO anfitrión: Kali Linux (CLI)

---

## ✅ Resultados clave

| Pregunta                                | Resultado                                                  |
|----------------------------------------|-------------------------------------------------------------|
| **Proceso malicioso identificado**     | `lssass.exe`                                                |
| **Ruta del ejecutable malicioso**      | `C:\Users\0XSH3R~1\AppData\Local\Temp\925e7e99c5\lssass.exe` |
| **IP del servidor C2**                 | `41.75.84.12`                                               |
| **Archivos descargados**               | `clip64.dll`, `cred64.dll`                                  |
| **Proceso que ejecuta los DLLs**       | `rundll32.exe`                                              |
| **Ruta de persistencia**               | `C:\Windows\System32\Tasks\lssass.exe`                      |

---

## 🧪 Técnicas y filtros

- Análisis de memoria RAM con `Volatility 3`
- Uso de filtros de strings para detección de descargas (`GET /`)
- Detección de tareas programadas como técnica de persistencia
- Técnicas MITRE ATT&CK identificadas:
  - `T1055.001 – DLL Injection`
  - `T1053.005 – Scheduled Task`
  - `T1071.001 – Application Layer Protocol: Web Traffic`

---

## 🧠 Reflexión personal

Este laboratorio fue útil para consolidar técnicas de análisis de memoria y detectar comportamiento malicioso incluso 
cuando se oculta tras nombres engañosos.  
Pude aplicar herramientas forenses con confianza y afianzar conceptos sobre persistencia y tráfico C2.  
En un entorno real, reforzaría la parte de análisis estático/dinámico de los binarios extraídos.

---

## 📁 Archivos

- [`Amadey Lab.docx`](./%20Amadey%20Lab%20.docx): Informe final del laboratorio

