# 🛡️ Reporte de Monitoreo de Red - Misión 236

## 🎯 Objetivo de la práctica
Monitorear en tiempo real el tráfico SSH entre un dispositivo móvil (Android/Termux) y el servidor central HP ProDesk.

## 🛠️ Herramientas utilizadas
- **Servidor:** Ubuntu Server 24.04 en HP ProDesk 600 G3.
- **Cliente:** Termux en Android con OpenSSH.
- **Analizador:** `tcpdump`.

## 💻 Comandos ejecutados

### 1. Identificación de interfaz
Se utilizó `ip a` para localizar la interfaz física:
`eno1`

### 2. Captura filtrada (Francotirador)
Comando para aislar el tráfico del celular (.72) hacia el puerto 22 del servidor (.238):
`sudo tcpdump -i eno1 src host 192.168.1.72 and port 22 -nn -v`

## 🕵️ Análisis de Evidencia
Se capturó la siguiente línea de tráfico:
`06:43:27.125310 IP 192.168.1.72.45820 > 192.168.1.238.22: Flags [P.], length 460`

**Interpretación técnica:**
- **Flag [P.]:** Indica un paquete "Push", enviando datos activos desde el celular.
- **Length 460:** Tamaño de la carga útil en bytes.
- **Puerto 45820:** Puerto efímero de salida del cliente Android.

## ✅ Conclusión
La conexión es estable y el firewall permite el tráfico SSH correctamente. El filtrado por IP de origen eliminó el ruido de red, permitiendo una monitorización limpia.
