# 🛡️ Laboratorio 236: Implementación de DNS Sinkhole con AdGuard Home

Este proyecto documenta la instalación, configuración y solución de problemas (troubleshooting) de un servidor de bloqueo de publicidad y rastreo a nivel de red, montado sobre un servidor **HP ProDesk 600 G3 Mini**.

## 📊 Especificaciones del Host
- **Hardware:** HP ProDesk 600 G3 Tiny (Core i5 7ma Gen, 16GB RAM).
- **OS:** Ubuntu Server 24.04 LTS.
- **Plataforma:** Docker & CasaOS.
- **Consumo Estimado:** 12W (~$35 MXN mensuales).

---

## 🛠️ Desafío Técnico: Conflicto de Puertos y Firewall

Durante la instalación, se presentaron conflictos con el puerto **53** (DNS) y el puerto **80** (Web). A continuación, se detalla la solución aplicada.

### 1. Liberación del puerto 53 (DNS)
Ubuntu utiliza `systemd-resolved`, el cual acaparaba el puerto 53 impidiendo que AdGuard Home filtrara el tráfico.

**Solución:**
```bash
sudo systemctl stop systemd-resolved
sudo systemctl disable systemd-resolved



sudo docker run -d --name adguard-home \
  -v /opt/adguardhome/work:/opt/adguardhome/work \
  -v /opt/adguardhome/conf:/opt/adguardhome/conf \
  -p 3000:3000/tcp \
  -p 53:53/udp \
  -p 53:53/tcp \
  --restart always \
  adguard/adguardhome


# 🛠️ Reporte Técnico: Resolución de Conflictos DNS (Puerto 53)
**Proyecto:** Laboratorio 236 - AdGuard Home
**Host:** HP ProDesk 600 G3 Mini (Ubuntu Server)

## ❌ Problema Identificado
El despliegue del contenedor Docker fallaba debido a que el puerto **53/tcp** ya estaba en uso por el servicio nativo de Ubuntu `systemd-resolved`.

## 🛡️ Pasos de Resolución (SOC Blue Team)

1. **Liberación de Interfaz:** Se desactivó el stub de DNS local para liberar el puerto 53.
   ```bash
   sudo systemctl stop systemd-resolved
   sudo systemctl disable systemd-resolved


---

### 💾 Cómo guardar y salir:
1.  **Pega el texto** (puedes usar el click derecho o `Ctrl+Shift+V` en tu terminal).
2.  Presiona **`Ctrl + O`** para guardar (te preguntará el nombre, solo dale **Enter**).
3.  Presiona **`Ctrl + X`** para salir y volver a la terminal.

### 🕵️ ¿Por qué este nombre?
Usar la extensión **`.md`** (Markdown) hará que cuando lo subas a GitHub, se vea con títulos grandes, negritas y bloques de código elegantes, en lugar de ser solo un texto plano aburrido.

**¿Quieres que te pase los comandos de Git uno por uno para subir este archivo específico a tu cuenta y que aparezca ya en tu perfil?** 🛡️🚀🔥
