# 🛡️ Análisis de Ataque APT en Active Directory: Simulación y Defensa

> **Proyecto Final - Curso Experto en Blue Team (250h)**
> *Simulación de adversario, Ingeniería de Detección (Sigma/Splunk) y Bastionado bajo normativa ENS/ISO 27001.*

---

## 📋 Resumen Ejecutivo

Este proyecto simula un **Ataque Persistente Avanzado (APT)** dirigido contra una infraestructura crítica basada en **Active Directory**. El objetivo fue replicar la "Kill Chain" completa de un adversario real para posteriormente diseñar, implementar y validar las defensas necesarias.

El trabajo cubre el ciclo de vida completo de la defensa:
1.  **Simulación:** Ejecución de TTPs usando **Atomic Red Team**.
2.  **Detección:** Análisis de logs (Sysmon) y creación de reglas **Sigma** convertidas a **Splunk (SPL)**.
3.  **Mitigación:** Propuesta de bastionado alineada con el **Esquema Nacional de Seguridad (ENS)** e **ISO 27001**.

---

## 🛠️ Stack Tecnológico

| Categoría | Herramientas Utilizadas |
| :--- | :--- |
| **Simulación de Ataques** | Atomic Red Team, Rubeus, Mimikatz, PowerShell |
| **Monitorización** | Sysmon (Event ID 1, 10, 11, etc.), Windows Event Logs |
| **SIEM & Detección** | **Splunk Enterprise**, Splunk Search Processing Language (SPL) |
| **Ingeniería de Reglas** | **Sigma Rules**, Sigma CLI (Conversión YAML -> SPL) |
| **Marco Normativo** | MITRE ATT&CK, Kill Chain, ENS, ISO/IEC 27001 |

---

## ⚔️ Kill Chain & Matriz MITRE ATT&CK

Se analizaron y ejecutaron las siguientes técnicas para comprometer el Controlador de Dominio:

| Fase (Táctica) | Técnica ID | Descripción del Ataque |
| :--- | :--- | :--- |
| **Acceso Inicial** | `T1566.001` | **Spearphishing Attachment:** Envío de adjunto malicioso (.xlsm) con macros. |
| **Ejecución** | `T1204.002` | **User Execution:** Activación del payload mediante interacción del usuario. |
| **Credenciales** | `T1558.003` | **Kerberoasting:** Solicitud masiva de tickets TGS para crackeo offline. |
| **Movimiento Lateral** | `T1550.002` | **Pass the Hash:** Autenticación remota usando hash NTLM (sin contraseña plana). |
| **Persistencia** | `T1547.001` | **Registry Run Keys:** Modificación del registro para ejecución automática al inicio. |
| **Persistencia** | `T1136.002` | **Create Account:** Creación de usuario backdoor en el dominio. |
| **Exfiltración** | `T1041` | **C2 Channel:** Robo de datos codificados en Base64 vía HTTP/S. |
| **Evasión** | `T1027` | **Obfuscation:** Uso de codificación para evadir firmas estáticas. |

---

## 🔍 Ingeniería de Detección: De Sigma a Splunk

Una de las partes clave del proyecto fue la **creación de reglas de detección agnósticas (Sigma)** y su compilación para nuestro SIEM (Splunk).

### Ejemplo 1: Detección de Kerberoasting (`T1558.003`)
*Detectamos un volumen anómalo de solicitudes de tickets TGS asociadas a herramientas como Rubeus.*

**Regla Sigma (YAML):**
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
