# 🛡️ Laboratorio 236: El Túnel Invisible (Tailscale)

**Objetivo:** Acceder al servidor desde cualquier parte del mundo (usando datos móviles) de forma segura, sin abrir puertos en el módem de la casa y manteniendo todo encriptado.

---

### 🍎 El Concepto: "El Túnel Secreto"
Imagina que tu servidor es una caja fuerte dentro de tu casa. 
* **Antes:** Solo podías abrirla si estabas físicamente en la sala.
* **El Problema:** Si abrías una ventana (puerto en el módem) para verla desde la calle, los ladrones (hackers) también podían ver esa ventana abierta.
* **La Solución (Tailscale):** Es como si instalaras un túnel secreto que conecta tu celular directamente con la caja fuerte. Nadie más ve el túnel, nadie más puede entrar, y no necesitas abrir ventanas en tu casa.

---

### 🛠️ Comandos de Instalación y Configuración

#### 1. Instalación del motor
Ejecutamos el script oficial para que el servidor entienda el lenguaje del túnel:
`curl -fsSL https://tailscale.com/install.sh | sh`

#### 2. Encendido y Vinculación
Para activar el túnel y decirle quién es el dueño, usamos:
`sudo tailscale up`
* Este comando nos da un link único. Al abrirlo y loguearnos con nuestra cuenta de Google, el servidor queda "amarrado" a nuestra red privada.

---

### 📱 Conexión del Dispositivo Remoto (Android)
Para que el túnel funcione, ambos lados deben tener la llave:
1. Instalamos la App de **Tailscale** en el celular.
2. Iniciamos sesión con la **misma cuenta de Google**.
3. Al encender el switch, el celular recibe una **IP Mágica (100.X.X.X)**.



---

### 🕵️ Análisis de Seguridad (Nivel SOC Blue Team)

* **Cifrado de Punto a Punto:** Los datos viajan encriptados. Si alguien intenta "escuchar" en un Wi-Fi público, solo verá ruido.
* **Sin Port Forwarding:** Al no abrir puertos en el router (módem), el servidor es invisible para los escaneos de bots en internet.
* **Autenticación Robusta:** La seguridad depende de nuestra cuenta de Google (que tiene verificación de dos pasos), lo que lo hace mucho más seguro que una simple contraseña.

---

### 📝 Resumen de IPs del Laboratorio 236
| Tipo de Conexión | Dirección IP | Cuándo usarla |
| :--- | :--- | :--- |
| **Local** | `192.168.1.238` | Cuando estés en el Wi-Fi de la casa. |
| **Remota (Túnel)** | `100.X.Y.Z` | Cuando estés con datos móviles o en otra red. |
