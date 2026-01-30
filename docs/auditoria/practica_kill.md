# 🛡️ Práctica: Cacería y Neutralización de Procesos (SIGKILL)

**Objetivo:** Aprender a identificar un proceso intruso y eliminarlo de forma definitiva.

---

### 🕵️ Paso 1: Crear el "Intruso"
Para simular un proceso sospechoso que se queda escondido, usamos:
`sleep 5000 &`
* *Nota:* El `&` lo manda al fondo para que siga corriendo sin bloquear nuestra terminal.

### 🔍 Paso 2: El Censo (Localizar al objetivo)
Usamos el "rastreador" para encontrar el número de identificación (PID) del intruso:
`ps aux | grep sleep`
* *Resultado:* Encontramos que el proceso tenía el **PID 1647**.

### 👊 Paso 3: El Golpe Maestro (Neutralización)
Para dar de baja al proceso sin que pueda oponer resistencia, usamos el nivel de fuerza máxima:
`kill -9 1647`
* *Explicación:* El `-9` (SIGKILL) le ordena al motor del sistema (Kernel) detener el proceso de inmediato.

### ✅ Paso 4: Verificación Final
Confirmamos que el pueblo está limpio volviendo a buscar:
`ps aux | grep sleep`
* *Resultado:* El proceso 1647 ya no existe. ¡Amenaza neutralizada!
