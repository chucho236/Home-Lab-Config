# 🛡️ Hardening de Servidor: Implementación de Firewall (UFW)

## 📝 Resumen Técnico
* **Analista:** chucho236
* **Fecha:** 26/01/2026
* **Objetivo:** Blindar el Nodo 01 (HP ProDesk) limitando el tráfico entrante.

---

## 🔒 Configuración de Perímetro
Se ha configurado el **Uncomplicated Firewall (UFW)** con las siguientes políticas:

1. **Default Deny:** Se bloquea todo el tráfico entrante por defecto.
2. **Acceso SSH (Puerto 22):** Se habilitaron reglas específicas para permitir la administración remota vía **IPv4** e **IPv6**.

## ✅ Verificación de Estado
El comando `sudo ufw status verbose` confirma que el firewall está **ACTIVO** y protegiendo el sistema contra accesos no autorizados.
