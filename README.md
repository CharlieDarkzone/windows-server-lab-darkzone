# Windows Server Lab – Darkzone

Laboratorio práctico de **administración de sistemas Windows Server**, enfocado en la
implementación de un **dominio Active Directory** en un entorno virtualizado con **QEMU/KVM**.

El proyecto documenta paso a paso la instalación, configuración y puesta en marcha
de un dominio Windows funcional, siguiendo buenas prácticas de sysadmin.

---

## 🧠 Objetivo del proyecto

- Aprender administración de **Windows Server 2022**
- Implementar un dominio **Active Directory**
- Configurar servicios básicos de infraestructura:
  - DNS
  - Gestión de usuarios y equipos
- Documentar el proceso de forma clara y reproducible
- Construir material para **portafolio personal**

---

## 🧱 Arquitectura del laboratorio

- Dominio: `darkzone.cl`
- Entorno virtualizado con QEMU/KVM
- Un controlador de dominio
- Un equipo cliente unido al dominio

📁 El diagrama de arquitectura se encuentra en la carpeta `diagrama/`.

---

## 🖥️ Componentes

### 🔹 Servidor (DC01)
- Sistema Operativo: Windows Server 2022
- Roles:
  - Active Directory Domain Services (AD DS)
  - DNS Server
- IP: 192.168.100.10 (estática)

### 🔹 Cliente (PC01)
- Sistema Operativo: Windows 10 Pro
- IP: Asignada por DHCP
- Unido al dominio `darkzone.cl`

---

## 📂 Estructura del repositorio

