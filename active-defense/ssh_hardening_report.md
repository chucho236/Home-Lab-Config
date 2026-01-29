# 🗝️🗝  Inplementacion de autentificacion por llaves de Hardering de SSH

## Objetivo de la practica
Fortalecer el acceso remoto al servidor **HP ProDesk 600 G3 (Home Lab)** mediante la eliminación de contraseñas vulnerables y la reducción de la superficie de ataque del servicio SSH.

## Implementacion de la tecnica 

### Fase A. Autentificacion por lalves (Key-Based Auth)
Se Genero un par de llaves criptograficas modernas para sustituir el uso de contraseñas tradicionales.
* **Algoritmo:** Ed25519 (proporciona mayor seguridad y mejor rendimiento que RSA).
* **Proceso:** La llave pública se transfirió al servidor mediante PowerShell, asegurando que solo el host autorizado (PC Principal) tenga acceso.

### Fase B: Modificación del Demonio SSH (sshd_config)
Se realizaron cambios profundos en `/etc/ssh/sshd_config` para endurecer el servicio:
* **Cambio de Puerto:** Se movió el servicio del puerto 22 al **2222** para mitigar escaneos automatizados y ataques de fuerza bruta masivos.
* **Desactivación de Root:** Se configuró `PermitRootLogin no` para evitar intentos de acceso directo al superusuario.
* **Prohibición de Contraseñas:** Se estableció `PasswordAuthentication no`, forzando el uso exclusivo de llaves SSH.

## 3. Bitácora de Troubleshooting (Resolución de Problemas)
Esta sección documenta los incidentes técnicos encontrados durante la implementación y sus soluciones, una habilidad clave para el rol de **SOC Blue Team**.

| Incidente | Causa Raíz | Solución |
| :--- | :--- | :--- |
| `Bad configuration option: PasswordAuthentication.` | Error de sintaxis (punto final inválido en el archivo de configuración). | Corrección de la línea 88 y validación con `sshd -t`. |
| `Missing privilege separation directory: /run/sshd` | El directorio temporal requerido por SSH no existía o fue borrado tras cambios de configuración. | Creación manual del directorio y configuración de persistencia mediante `tmpfiles.d`.|
| Fallo al reiniciar el servicio | Conflicto con el firewall o sintaxis errónea. | Habilitación de regla en UFW (`allow 2222/tcp`) y reinicio forzado del demonio. |

## 4. Verificación de Seguridad
Se confirmó la operatividad del servicio mediante el comando:
`ss -tunlp | grep 2222`

**Resultado:** El servidor escucha correctamente en el puerto 2222 bajo el protocolo TCP.

## 5. Conclusión
El servidor ahora opera bajo un modelo de **Zero Trust** para accesos SSH, donde el conocimiento de la IP y el puerto no es suficiente para ingresar; se requiere obligatoriamente la posesión de la llave privada física del administrador.
