# 💽 Optimización: Expansión de Disco Duro en Caliente

**Escenario:** Instalamos Linux y notamos que solo detecta una parte del disco duro (ej. 80GB de 240GB). El resto del espacio está "dormido".

---

### 🍎 Concepto: "Agrandar la casa sin tumbar las paredes"
Imagina que compraste un terreno de 240 metros (Disco Físico), pero tu casa solo mide 80 metros (Partición). Este proceso sirve para estirar las paredes de la casa hasta que ocupen todo el terreno, ¡y lo mejor es que lo hacemos mientras estamos adentro (con el sistema encendido)!

---

### 🛠️ Paso 1: Diagnóstico (¿Dónde estamos parados?)
Antes de mover nada, usamos el comando para ver el mapa de las particiones:
`lsblk`

* **Peras y Manzanas:** Aquí vimos que el disco `sda` era grande, pero la partición `sda2` era pequeña. Identificamos que nos sobraba espacio.

---

### 🛠️ Paso 2: Agrandar la "Caja" (Partición física)
Usamos la herramienta para estirar la partición número 2 del disco `sda`:
`sudo growpart /dev/sda 2`

* **¿Qué hace esto?**: Toma la "cerca" de la partición y la mueve hasta el final del disco duro. 
* **Nota del Inge:** Si no tienes el comando, se instala con `sudo apt install cloud-guest-utils`.

---

### 🛠️ Paso 3: Estirar el "Piso" (Sistema de archivos)
Ya tenemos la cerca más grande, pero el piso (donde guardamos archivos) sigue siendo chico. Lo estiramos con:
`sudo resize2fs /dev/sda2`

* **Peras y Manzanas:** Es como decirle al sistema operativo: "Ya tienes permiso de caminar por todo el terreno nuevo, ¡ocúpalo!".

---

### ✅ Verificación Final
Para confirmar que ahora tenemos los 234GB listos para nuestra Nube Privada, usamos:
`df -h`

---

## 💡 ¿Por qué es útil para un Administrador?
En una empresa, los servidores suelen quedarse sin espacio porque crecen las bases de datos o los logs. Saber expandir el disco sin apagar el servidor (en caliente) es una habilidad de "Nivel Pro" que evita que el servicio se detenga.
