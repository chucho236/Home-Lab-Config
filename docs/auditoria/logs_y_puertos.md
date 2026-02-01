# 🕵️ Práctica: Auditoría de Logs y Puertos Internos

**Objetivo:** Interpretar el rastro de actividades en el sistema y verificar qué servicios están escuchando en la red.

---

### 📜 1. Análisis de `auth.log`
Aprendimos a leer las líneas de auditoría del sistema:
* **TTY (pts/0):** Identifica la terminal virtual del usuario conectado por SSH.
* **PWD:** Muestra la carpeta donde estaba parado el usuario al ejecutar el comando.
* **COMMAND:** Registra la ruta completa del binario ejecutado (ej. `/usr/sbin/ufw`).

### 🔌 2. Escaneo de Puertos Locales
Usamos `sudo ss -lnpt` para ver las puertas abiertas en modo "Escucha" (LISTEN).
* **Puerto 2222:** Confirmado como el único acceso externo abierto para administración.
* **Puerto 53 (Loopback):** Servicio interno de DNS necesario para que el servidor navegue en internet. No es accesible desde el exterior.

---

## ✅ Conclusión
El servidor no presenta "puertas traseras" abiertas. Todas las ejecuciones de comandos administrativos (sudo) quedan registradas con fecha, hora y ruta exacta, facilitando el rastreo en caso de un incidente de seguridad.

