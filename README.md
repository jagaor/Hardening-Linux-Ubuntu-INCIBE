# Bastionado de Sistema Linux (Hardening)

## 📝 Descripción General
Este proyecto forma parte del módulo de "Bastionado de Redes y Sistemas" y tiene como objetivo principal la fortificación (hardening) de un servidor Linux desde cero. Tomando como referencia las guías de securización del INCIBE y otras buenas prácticas del sector, se ha desplegado un entorno seguro, aplicando más de 25 controles técnicos para minimizar la superficie de ataque y garantizar la integridad, confidencialidad y disponibilidad del sistema.

## 🎯 Objetivos del Proyecto
* Desplegar un servidor Ubuntu Server en un entorno virtualizado (VirtualBox).
* Aplicar guías de buenas prácticas y políticas de securización estandarizadas (INCIBE).
* Securizar el acceso remoto mediante el endurecimiento del servicio SSH (cambio de puerto, autenticación por claves).
* Implementar medidas de protección activa contra ataques de fuerza bruta.
* Configurar políticas estrictas para la gestión de usuarios y contraseñas.
* Auditar el nivel de seguridad del sistema antes y después del bastionado para cuantificar las mejoras.

## 🛠️ Tecnologías y Herramientas
* **Sistema Operativo**: Ubuntu Server 24.04 LTS.
* **Entorno de Virtualización**: VirtualBox.
* **Seguridad Perimetral y Acceso**: UFW (Firewall), OpenSSH, Fail2ban.
* **Control de Acceso Obligatorio (MAC)**: AppArmor.
* **Auditoría y Pruebas**: Lynis (Auditoría de seguridad), Nmap (Escaneo de puertos).
* **Mantenimiento**: Unattended-upgrades (Actualizaciones automáticas de seguridad).

## ⚙️ Detalles de Implementación Destacados
* **Bastionado de SSH y Red**: Se modificó el puerto por defecto de SSH (ej. 2222), deshabilitando el acceso para el usuario `root` y forzando la autenticación exclusiva mediante intercambio de claves criptográficas. El firewall se configuró con políticas de denegación por defecto, abriendo solo los puertos estrictamente necesarios.
* **Protección Activa con Fail2ban**: Se configuraron *jails* específicos para monitorizar los registros de autenticación, logrando banear automáticamente las direcciones IP tras detectar múltiples intentos de inicio de sesión fallidos.
* **Políticas de Usuarios**: Se aplicaron restricciones de caducidad y complejidad de contraseñas utilizando herramientas como `chage`, asegurando el cumplimiento de políticas de rotación de credenciales.
* **Auditoría con Lynis**: Se ejecutó la herramienta de auditoría Lynis tras aplicar las medidas de bastionado, logrando una puntuación de seguridad (Hardening Index) superior al 80%, confirmando la eficacia de las configuraciones aplicadas.

## 📄 Documentación Completa
Para revisar el paso a paso de la configuración, los comandos exactos utilizados para aplicar cada política de seguridad y las evidencias de los escaneos de Nmap y Lynis, puedes consultar la memoria técnica del proyecto:

👉 [Enlace al Informe Técnico en Google Drive](https://docs.google.com/document/d/13uwng1Izg0a-1deT3gKJf81nPvCtGj8Sz_PDhY7Lw2k/edit?usp=sharing)

## ⚠️ Aviso Legal / Ética
*Las técnicas de bastionado y auditoría documentadas en este repositorio se han aplicado sobre un entorno de laboratorio local. Las prácticas de fortificación son esenciales para la administración de sistemas en producción y se han realizado con un enfoque estrictamente defensivo (Blue Teaming).*
