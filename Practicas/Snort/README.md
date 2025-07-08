 # 🛡️ Práctica: Instalación y Configuración de Snort como NIDS

**Curso:** DFIR – Digital Forensic and Incident Response  
**Módulo:** Respuesta ante Incidentes  
**Tipo de actividad:** Práctica grupal evaluable  
**Participantes:** Juan Carlos Vico, Joan Navinés, Ignacio Camacho, Jesica Julia Olortegui, Luis Delgado

---

## 🎯 Descripción

Esta práctica consistió en la **instalación y configuración de Snort** como un sistema de detección de intrusos en red (NIDS), desplegado sobre una máquina virtual con Parrot OS. Se diseñaron y ejecutaron varios escenarios de detección mediante reglas personalizadas que simulan actividades maliciosas o sospechosas comunes en entornos reales.

---

## 🛠️ Actividades realizadas

- Instalación de Parrot OS en VirtualBox
- Configuración avanzada de repositorios y claves GPG
- Instalación y configuración de Snort 2.9.7
- Montaje de laboratorio de red con Parrot OS y Windows 10
- Ajustes de red, firewall y conectividad ICMP
- Ejecución de reglas personalizadas con alertas en tiempo real

---

## 🔍 Reglas y casos de uso implementados

| Caso de uso                         | Tipo de regla y técnica |
|------------------------------------|--------------------------|
| 🔔 ICMP a 8.8.8.8                   | Detección de pings         |
| 🌐 Tráfico web (HTTP/HTTPS)        | Puertos 80, 443, 8080     |
| ☁️ Conexión a Dropbox              | Por contenido, TLS SNI e IP |
| 🔑 Conexiones salientes por SSH    | Puerto 22, tráfico saliente |

Cada regla fue comprobada, ajustada y verificada mediante logs en `/var/log/snort/alert`.

---

## 💡 Detalles técnicos

- Interfaz de red configurada: `enp0s3`
- Dirección local de escucha: `10.0.2.0/24`
- Servicios monitorizados: Web, SSH, Ping, Cloud Apps
- Reglas definidas en: `/etc/snort/rules/local.rules`

---

## 📁 Archivos

- [`Práctica-SNORT.pdf`](./Práctica-SNORT.pdf): Informe completo con explicación paso a paso, comandos utilizados, reglas personalizadas y resultados de ejecución.

---

## 🧠 Reflexión personal

Esta práctica me permitió profundizar en el funcionamiento real de un sistema IDS en red, desde su instalación hasta su uso en un entorno práctico. Las reglas desarrolladas mostraron cómo detectar múltiples tipos de tráfico, lo cual refuerza tanto el conocimiento técnico de red como la capacidad de reacción ante incidentes.

Aprendí a solucionar problemas reales como errores de versión, conflictos con repositorios o ajustes del firewall, lo cual fue clave para conseguir un entorno funcional. Snort se presenta como una herramienta fundamental para cualquier profesional de seguridad defensiva.
