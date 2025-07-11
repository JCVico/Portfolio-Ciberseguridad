
# 🌐 Práctica: Segmentación de redes con Cisco Packet Tracer

**Curso:** DFIR – Digital Forensic and Incident Response  
**Módulo:** II  
**Herramienta utilizada:** Cisco Packet Tracer  
**Tipo de actividad:** Práctica evaluable

---

## 🎯 Descripción

Diseño y configuración de una red segmentada en VLANs mediante Cisco Packet Tracer.
Se parte de un escenario simulado con tres departamentos que requieren aislamiento
lógico, pero comunicación entre ellos a través de un router con subinterfaces.

---

## 🛠️ Actividades realizadas

- Diseño de red con 3 VLANs:
  - Contabilidad (`192.168.1.0/24`)
  - Administración (`192.168.2.0/24`)
  - Servidores (`192.168.3.0/24`)
- Configuración de puertos del switch según VLAN
- Creación y asignación de subinterfaces en el router
- IPs estáticas asignadas a PCs y servidores
- Cableado y configuración del hardware virtual
- Verificación de conectividad con pruebas `ping`

---

## 🖥️ Aspectos técnicos destacados

| Elemento            | Configuración                            |
|---------------------|------------------------------------------|
| VLAN 1 (Contabilidad)    | Puertos F0/1 a F0/4 → 192.168.1.x       |
| VLAN 2 (Administración)  | Puertos F0/5 a F0/8 → 192.168.2.x       |
| VLAN 3 (Servidores)      | Puertos F0/9 a F0/12 → 192.168.3.x      |
| Router Interfaces        | Subinterfaces configuradas como gateway |
| Verificación             | Pings exitosos entre VLANs              |

---

## 📁 Archivos

- [`Práctica-Cisco-Packet-Tracer.pdf`](./Práctica-Cisco-Packet-Tracer.pdf): Informe con topología, configuraciones e IPs.
