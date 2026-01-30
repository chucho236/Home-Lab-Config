# 🛡️ Práctica: Monitoreo de Red y Control de Firewall (UFW)

**Objetivo:** Identificar conexiones activas, entender la jerarquía de procesos SSH y aprender a bloquear IPs sospechosas.

---

### 🕵️ Paso 1: Activar el Radar de Red
Para ver quién está conectado al servidor en tiempo real, usamos:
`sudo ss -tunp`

**¿Qué significan las siglas?**
* **t/u:** Conexiones TCP y UDP.
* **n:** Muestra números de IP (no nombres).
* **p:** Muestra el programa y el PID (identificador del proceso).

### 🔍 Paso 2: Análisis de Conexión (Caso SSH)
En la auditoría se detectó una conexión establecida (`ESTAB`) en el puerto **2222**.
* **Dato Técnico:** Aparecen dos PIDs (ej. 1320 y 1391). El primero mantiene el túnel abierto y el segundo es el proceso "hijo" que atiende al usuario.
* **FD (File Descriptor):** Linux asigna un número (ej. fd=4) para identificar ese "cable virtual" como si fuera un archivo.

### 🧱 Paso 3: Bloqueo de Amenazas (Firewall)
Si identificamos una IP maliciosa (ej. `1.1.1.1`), procedemos a bloquearla para que no pueda ni tocar la puerta:
`sudo ufw deny from 1.1.1.1`

Para verificar la lista de bloqueos con su índice numérico:
`sudo ufw status numbered`

### 🔓 Paso 4: Gestión de Reglas (Desbloqueo)
Para eliminar una regla de forma rápida usando su número de renglón (ej. el renglón 3):
`sudo ufw delete 3`

---

## ✅ Conclusión
Se logró entender la diferencia entre "matar un proceso" (`kill`) y "bloquear una IP" (`ufw`). Mientras que kill saca al intruso, el firewall evita que regrese.
