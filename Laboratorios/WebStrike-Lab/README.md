# 🧪 Laboratorio – CyberDefenders: WebStrike Lab

**Fecha de realización:** 27/05/2025  
**Plataforma:** CyberDefenders  
**Duración estimada:** 30 minutos  
**Nivel de dificultad:** Fácil

---

## 🎯 Descripción

Este laboratorio simula una intrusión web en la que un atacante aprovecha una funcionalidad de subida de archivos para cargar una web shell camuflada como imagen. A través del tráfico de red capturado, se investiga el proceso de carga, ejecución de la shell y la posterior exfiltración de información del sistema.

---

## 🛠️ Herramientas utilizadas

- **Wireshark**: Análisis de tráfico de red
- **Linux VM**: Entorno de simulación
- **PCAP**: Archivo de captura proporcionado

---

## 🔍 Resultados clave

| Pregunta | Resultado |
|---------|-----------|
| **Ciudad de origen del ataque** | Tianjin |
| **User-Agent del atacante** | `Mozilla/5.0 (X11; Linux x86_64; rv:109.0)...` |
| **Nombre de la web shell** | `image.jpg.php` |
| **Directorio de subida** | `/reviews/uploads/` |
| **Puerto externo usado** | `8080` |
| **Archivo exfiltrado** | `/etc/passwd` |

---

## 🧪 Técnicas y filtros aplicados en Wireshark

- Filtros HTTP:
  - `http.request.method == POST`
  - `http.request.uri contains "image.jpg.php"`
  - `http contains "passwd"`

- Análisis de cabeceras:
  - User-Agent
  - IP de origen
  - URI y payload de subida

- Identificación de puerto de reverse shell:
  - `tcp.dstport == 8080`

---

## 🧠 Reflexión personal

Este laboratorio me permitió entender cómo una vulnerabilidad aparentemente simple (como subir un archivo) puede ser explotada para tomar control de un servidor. La importancia de analizar capturas de red con precisión, reconocer patrones de comportamiento malicioso y filtrar adecuadamente con Wireshark fue clave en todo el proceso.

Además, reforzó la necesidad de implementar controles como validación de archivos, restricción de extensiones y análisis de tráfico saliente en entornos reales.

---

## 📁 Archivos

- [`WebStrike Lab.odt`](../WebStrike Lab.odt): Informe original del laboratorio


