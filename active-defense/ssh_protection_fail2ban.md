 Implementacion de Defensa Activa fail2Ban

## 🎯 Objetivo
Proteger el acceso SSH del servidor HP ProDesk contra ataques de fuerza bruta, automatizando el bloqueo de direcciones IP tras múltiples intentos fallidos de inicio de sesión.

## 🛠️ Herramientas y Comandos
- **Servicio:** `fail2ban`
- **Instalación:**
  `sudo apt update && sudo apt install fail2ban -y`

## ⚙️ Configuración Realizada
Se creó un archivo de configuración local en `/etc/fail2ban/jail.local` para evitar sobreescribir las configuraciones por defecto del sistema.

### Parámetros de la "Cárcel" (Jail) para SSH:
```ini
[sshd]
enabled = true
port = 22
filter = sshd
logpath = /var/log/auth.log
maxretry = 3
findtime = 10m
bantime = 1h
