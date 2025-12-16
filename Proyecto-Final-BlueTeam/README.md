# 🛡️ Análisis de Ataque APT en Active Directory: Simulación y Defensa

> **Proyecto Final - Curso Experto en Blue Team (250h)**
> *Simulación de adversario, Ingeniería de Detección (Sigma/Splunk) y Bastionado bajo normativa ENS/ISO 27001.*

---

## 📋 Resumen Ejecutivo

Este proyecto simula un **Ataque Persistente Avanzado (APT)** dirigido contra una infraestructura crítica basada en **Active Directory**. El objetivo fue replicar la *Kill Chain* completa de un adversario real para posteriormente diseñar, implementar y validar las defensas necesarias.

El trabajo cubre el ciclo de vida completo de la defensa:

1. **Simulación:** Ejecución de TTPs usando **Atomic Red Team**.
2. **Detección:** Análisis de logs (Sysmon) y creación de reglas **Sigma** convertidas a **Splunk (SPL)**.
3. **Mitigación:** Propuesta de bastionado alineada con el **Esquema Nacional de Seguridad (ENS)** e **ISO/IEC 27001**.

---

## 🛠️ Stack Tecnológico

| Categoría                 | Herramientas Utilizadas                                        |
| :------------------------ | :------------------------------------------------------------- |
| **Simulación de Ataques** | Atomic Red Team, Rubeus, Mimikatz, PowerShell                  |
| **Monitorización**        | Sysmon (Event ID 1, 10, 11, etc.), Windows Event Logs          |
| **SIEM & Detección**      | **Splunk Enterprise**, Splunk Search Processing Language (SPL) |
| **Ingeniería de Reglas**  | **Sigma Rules**, Sigma CLI (Conversión YAML → SPL)             |
| **Marco Normativo**       | MITRE ATT&CK, Kill Chain, ENS, ISO/IEC 27001                   |

---

## ⚔️ Kill Chain & Matriz MITRE ATT&CK

Se analizaron y ejecutaron las siguientes técnicas para comprometer el Controlador de Dominio:

| Fase (Táctica)         | Técnica ID  | Descripción del Ataque                                                                |
| :--------------------- | :---------- | :------------------------------------------------------------------------------------ |
| **Acceso Inicial**     | `T1566.001` | **Spearphishing Attachment:** Envío de adjunto malicioso (.xlsm) con macros.          |
| **Ejecución**          | `T1204.002` | **User Execution:** Activación del payload mediante interacción del usuario.          |
| **Credenciales**       | `T1558.003` | **Kerberoasting:** Solicitud masiva de tickets TGS para crackeo offline.              |
| **Movimiento Lateral** | `T1550.002` | **Pass the Hash:** Autenticación remota usando hash NTLM (sin contraseña en claro).   |
| **Persistencia**       | `T1547.001` | **Registry Run Keys:** Modificación del registro para ejecución automática al inicio. |
| **Persistencia**       | `T1136.002` | **Create Account:** Creación de usuario backdoor en el dominio.                       |
| **Exfiltración**       | `T1041`     | **C2 Channel:** Robo de datos codificados en Base64 vía HTTP/S.                       |
| **Evasión**            | `T1027`     | **Obfuscation:** Uso de codificación para evadir firmas estáticas.                    |

---

## 🔍 Ingeniería de Detección: De Sigma a Splunk

Una de las partes clave del proyecto fue la **creación de reglas de detección agnósticas (Sigma)** y su compilación para el SIEM (**Splunk**).

### Ejemplo 1: Detección de Kerberoasting (`T1558.003`)

*Detección de un volumen anómalo de solicitudes de tickets TGS asociadas a herramientas como Rubeus.*

#### Regla Sigma (YAML)

```yaml
title: Detección de Kerberoasting (Rubeus/Invoke-Kerberoast)
status: experimental
logsource:
  product: windows
  service: sysmon
detection:
  selection:
    CommandLine|contains:
      - 'rubeus'
      - 'kerberoast'
  condition: selection
level: high
```

#### Consulta SPL generada (Splunk)

```spl
index=* source="*sysmon*" EventCode=1 (
  ("rubeus" AND "kerberoast") OR "Invoke-Kerberoast"
)
```

---

### Ejemplo 2: Detección de Persistencia (`T1547.001`)

*Detección del uso de `reg add` para inyectar binarios en claves de arranque `Run` o `RunOnce`.*

#### Consulta SPL implementada

```spl
index=* source="*sysmon*" EventCode=1 Image="*\\reg.exe"
(CommandLine="*CurrentVersion\\Run*" OR CommandLine="*CurrentVersion\\RunOnce*")
CommandLine="*reg add*"
```

---

## 🛡️ Bastionado y Cumplimiento Normativo

Más allá de la detección, se propusieron medidas de **Hardening** correlacionadas con normativas oficiales:

* **Protección contra Phishing**
  Bloqueo de extensiones peligrosas (.exe, .scr, macros) y despliegue de DMARC/SPF.
  *(ENS: MP.COM.1)*

* **Mitigación de Kerberoasting**
  Uso de contraseñas de +25 caracteres para cuentas de servicio y adopción de **gMSA**.
  *(ISO/IEC 27001: A.9.2.5)*

* **Reducción de Superficie de Ataque (ASR)**
  Reglas para impedir que Microsoft Office lance procesos hijos (PowerShell, cmd).

* **Control de Acceso**
  Restricción de NTLM y eliminación de privilegios de administrador local siguiendo el **Principio de Mínimo Privilegio**.

---

## 📂 Documentación Completa del Proyecto

Este repositorio contiene la documentación detallada con evidencias, logs y procedimientos paso a paso:

* 📄 **Informe Técnico Completo (PDF)**
  Análisis detallado (~40 páginas) con evidencias de Sysmon y Splunk.

* 📊 **Presentación Ejecutiva (PDF)**
  Resumen visual de la Kill Chain, técnicas utilizadas y resultados.

---

### 👥 Integrantes del Proyecto

**Proyecto final del curso Experto en Blue Team**
Organizado por **Fundación ONCE**, **Por Talento Digital** e **INCIBE**.

📁 **Trabajo realizado en grupo por:**
* Marta Fernández
* Juan Carlos Vico (autor del repositorio)

---

Este proyecto demuestra la capacidad de **traducir amenazas teóricas en defensas prácticas y operativas**, alineadas con estándares reales de seguridad.
