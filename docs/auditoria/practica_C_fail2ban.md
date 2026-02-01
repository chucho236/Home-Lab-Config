# 🛡️ Práctica C: Configuración de Defensa Activa (Fail2Ban)

**Objetivo:** Instalar y configurar un "guardián automático" que monitoree los intentos de acceso y bloquee a los atacantes (robots o hackers) que intenten adivinar nuestra contraseña.

---

### 🍎 Concepto: "El Cadenero Automático"
Si la **Práctica A** fue aprender a leer las huellas (logs) y la **Práctica B** fue cerrar las puertas (Firewall), esta **Práctica C** es poner a un guardia que lea las huellas en tiempo real y cierre la puerta automáticamente si detecta a un sospechoso.

---

### 🛠️ Paso 1: Instalación del servicio
Utilizamos el siguiente comando para bajar las herramientas:
`sudo apt update && sudo apt install fail2ban -y`

* **sudo**: Permisos de administrador.
* **apt update**: Actualiza la lista de "la tienda" de apps.
* **install fail2ban**: Instala el programa guardián.
* **-y**: Confirma que sí a todo automáticamente.

---

### 🛠️ Paso 2: Creación del manual personalizado
Nunca editamos el archivo original por seguridad, así que creamos una copia de trabajo:
`sudo cp /etc/fail2ban/jail.conf /etc/fail2ban/jail.local`

* **Peras y Manzanas:** Es como sacar una fotocopia del manual de fábrica para poder rayarlo y hacerle cambios sin arruinar el original.

---

### 🛠️ Paso 3: Configuración de las Reglas de Combate
Editamos el archivo con `sudo nano /etc/fail2ban/jail.local` y configuramos el bloque `[sshd]` de la siguiente manera:

```bash
[sshd]
enabled = true
port    = 2222
maxretry = 3
findtime = 10m
bantime = 1h
