## 🛡️ Reporte Técnico: Análisis de Puertos con ss
# Descripcion del Analisis: Se Realizo una inspeccion de los dockets activos en el Nodo 01 (HP Prodesk) Para Verificar que solo los servicios autorizados esten comunicandose con la RED.

Puertos identificados y Funciones

* Puerto 22 (TCP) Servicio SSH Activo para administracion remota segura (IPv4) e IPv6)
* Puerto 53 (TCP/UDP): Servicio DNS interno (systemd-resolved) para la resolución de nombres de dominio.
* Puertos 68/546 (UDP): Protocolo DHCP encargado de gestionar la dirección IP asignada por el módem.

Conclusión de Seguridad: El estado de las conexiones es ÓPTIMO. Todos los puertos identificados corresponden a servicios base del sistema y comunicación necesaria de red, sin detectarse procesos desconocidos o sospechosos.


