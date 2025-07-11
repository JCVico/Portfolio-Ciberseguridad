# 🧪 Laboratorio – CyberDefenders: Oski Lab

**Fecha de realización:** 27/05/2025  
**Plataforma:** CyberDefenders  
**Duración estimada:** 45 minutos  
**Nivel de dificultad:** Media

---

## 🎯 Descripción

Este laboratorio simula una situación real en la que un empleado abre un
archivo malicioso (.PPT) enviado por correo. El objetivo es analizar el
comportamiento del archivo, identificar el malware y entender sus técnicas de
persistencia, evasión y exfiltración.

---

## 🔍 Objetivos del análisis

- Identificar la **familia del malware** embebido en el archivo
- Analizar la **fecha de creación**, el **servidor C2C** y las **librerías utilizadas**
- Determinar la técnica **MITRE ATT&CK** empleada
- Extraer datos como la **clave RC4** y observar el proceso de **autoeliminación**

---

## 🛠️ Herramientas utilizadas

- [VirusTotal](https://www.virustotal.com/)
- [ANY.RUN](https://app.any.run/)
- [Recorded Future Triage](https://triage.recordedfuture.com/)

---

## ✅ Resultados clave

| Pregunta                   | Resultado                                          |
|---------------------------|----------------------------------------------------|
| **Familia del malware**   | Stealc                                             |
| **Fecha de creación**     | 2022-09-28 17:40:46 UTC                            |
| **Servidor C2C**          | `http://171.22.28.221/5c06c05b7b34e8e6.php`        |
| **Primera DLL cargada**   | `sqlite3.dll`                                      |
| **Clave RC4**             | `5329514621441247975720749009`                     |
| **MITRE ATT&CK**          | T1555 – Credentials from Password Stores           |
| **Ruta de eliminación**   | `C:\ProgramData`                                   |
| **Autoeliminación**       | 5 segundos tras exfiltración                       |

---

## 🧠 Reflexión personal

Este laboratorio fue especialmente interesante porque permitió aplicar
conocimientos prácticos sobre análisis de malware combinando análisis estático
y dinámico. Ver cómo el malware usa DLLs legítimas y se autoelimina tras la
exfiltración fue clave para entender su sofisticación.

Herramientas como ANY.RUN y VirusTotal facilitaron el proceso de descubrimiento.

---

## 📁 Archivos

- [`OSKI LAB.docx`](../OSKI-LAB.docx): Informe original del laboratorio
