# Reporte de Auditoría: Monitoreo de Procesos (Hunting)

**Fecha:** 30 de enero de 2026
**Analista:** Chucho (delmogar)
**Sistema:** Ubuntu Server (HP ProDesk 600 G3)

## 1. Objetivo
Identificar procesos sospechosos, verificar el consumo de recursos y asegurar que los servicios de seguridad (Fail2Ban) estén operando correctamente.

## 2. Metodología
Se utilizó el comando `ps` para listar procesos ordenados por consumo de memoria y `lsof` para auditar archivos abiertos por procesos críticos.

## 3. Hallazgos
* **Proceso Líder:** `fail2ban-server` (PID 876). Consumo de RAM estable (0.2%).
* **Integridad del Kernel:** Los procesos `kworker` fueron auditados. Se confirmó que todos corren bajo el usuario `root` y están encerrados en corchetes `[]`, validando su legitimidad como hilos del kernel.
* **Conexiones SSH:** Se identificaron 3 procesos `sshd` activos, correspondientes a las sesiones de administración actuales.

## 4. Conclusiones
El sistema no presenta anomalías. No se detectaron procesos "huérfanos" ni ejecutables corriendo desde carpetas temporales (`/tmp` o `/dev/shm`).
