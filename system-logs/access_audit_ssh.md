# 📊 Auditoría de Logs: Análisis de Accesos SSH

## 🎯 Objetivo
Identificar intentos de acceso no autorizados y patrones de ataque mediante el análisis del archivo de registro de autenticación del sistema `/var/log/auth.log`.

## 🛠️ Comandos de Auditoría Utilizados

### 1. Rastreo de Intentos Fallidos
Se filtraron los registros para localizar errores de contraseña, lo que indica posibles ataques de fuerza bruta.
`sudo grep "Failed password" /var/log/auth.log`

### 2. Extracción Avanzada de IPs (RegEx)
Para obtener un reporte limpio, se implementó una **Expresión Regular** que extrae únicamente las direcciones IP, ignorando el resto del texto.

**Comando Pro:**
`sudo grep "Failed password" /var/log/auth.log | grep -oE "[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}" | sort | uniq -c | sort -nr`



## 📈 Resultados Obtenidos
En el análisis del laboratorio, se detectaron los siguientes eventos:
- **IP Identificada:** 192.168.1.67
- **Frecuencia:** 1 intento fallido.
- **Usuario atacado:** chucho236

## ✅ Conclusión
La auditoría de logs es la base de la ciber-forense. Gracias a estos filtros, podemos identificar atacantes recurrentes y proceder al bloqueo.
