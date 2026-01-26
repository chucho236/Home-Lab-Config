# 🛡️ Reporte de Incidente - Laboratorio SOC

## 📝 Detalles Generales
* **Analista:** chucho236
* **Fecha:** 26/01/2026
* **Dispositivo:** Nodo 01 (HP ProDesk)

---

## 🔍 Diagnóstico
Se detectó que el servidor no tenía conectividad a la red. Al ejecutar el comando `ip a`, no se visualizaba una dirección IPv4 asignada.

## ✅ Resolución
Se procedió a revisar la **Capa 1** (Capa Física). Se encontró el cable Ethernet desconectado. Tras la conexión física, el servidor obtuvo exitosamente la IP `192.168.1.238`.LOG DE INCIDENCIAS - NODO 01 Fecha: 26/01/2026 Analista: chucho236 Evento: Error de conectividad en Capa 1 (Capa Física). Solución: Se conectó cable Ethernet físico. El comando ip a validó la IP 192.168.1.238.
