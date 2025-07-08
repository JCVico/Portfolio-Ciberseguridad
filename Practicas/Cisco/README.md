 
# 🌐 Práctica: Segmentación de redes con Cisco Packet Tracer

**Curso:** DFIR – Digital Forensic and Incident Response  
**Módulo:** II  
**Herramienta utilizada:** Cisco Packet Tracer  
**Tipo de actividad:** Práctica evaluable

---

## 🎯 Descripción

Esta práctica tiene como objetivo el diseño y configuración de una red segmentada en VLANs utilizando Cisco Packet Tracer. Se parte de un escenario simulado con tres departamentos que requieren aislamiento lógico, pero conectividad entre ellos a través de un router con interfaces virtuales.

---

## 🛠️ Actividades realizadas

- Diseño de red con 3 VLANs:
  - Contabilidad (`192.168.1.0/24`)
  - Administración (`192.168.2.0/24`)
  - Servidores (`192.168.3.0/24`)
- Configuración de puertos del switch asignados a cada VLAN
- Creación y asignación de interfaces VLAN en el router
- Asignación de IPs estáticas a PCs y servidores
- Cableado de red y configuración del hardware virtual
- Verificación de conectividad con pruebas de `ping` entre dispositivos

---

## 🖥️ Aspectos técnicos destacados

| Elemento      | Configuración                       |
|---------------|-------------------------------------|
| VLAN 1 (Contabilidad) | Puertos F0/1 a F0/4 → 192.168.1.x |
| VLAN 2 (Administración) | Puertos F0/5 a F0/8 → 192.168.2.x |
| VLAN 3 (Servidores) | Puertos F0/9 a F0/12 → 192.168.3.x |
| Router Interfaces | 1 por VLAN configuradas con IP gateway |
| Verificación | Pings exitosos entre equipos de distintas VLANs |

---

## 📁 Archivos

- [`Práctica-Cisco-Packet-Tracer.pdf`](./Práctica-Cisco-Packet-Tracer.pdf): Informe detallado con explicación de la topología, IPs, configuración y pruebas realizadas.
---
