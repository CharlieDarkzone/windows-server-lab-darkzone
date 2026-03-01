## 🎯 Objetivo

Documentar el modelo implementado para la gestión de excepciones de políticas (GPO), específicamente en el caso del bloqueo de dispositivos USB.

Este modelo permite mantener la arquitectura base del dominio sin realizar modificaciones directas en las políticas globales.

---

## 🏗️ Política Base

Se definió una política de seguridad:

**GPO:** `Bloqueo USB`  
Aplicada a: `OU = Equipos`  
Filtrada a: `Equipos-Callcenter`  

Configuración aplicada:

---
Computer Configuration
└── Administrative Templates
└── System
└── Removable Storage Access
└── All Removable Storage classes: Deny all access
---

Esta GPO establece el bloqueo total de dispositivos USB para equipos del Callcenter.

---

## ⚠️ Problema

En entornos reales pueden surgir solicitudes temporales de excepción, por ejemplo:

- Transferencia controlada de archivos
- Soporte técnico específico
- Requerimiento operacional justificado

Modificar directamente la GPO base implicaría:

- Alterar la postura de seguridad global
- Generar riesgo de impacto masivo
- Romper la consistencia de la arquitectura
- Perder trazabilidad clara de la excepción

---

## 🧠 Modelo Implementado

Se adopta un modelo basado en grupos de seguridad.

### 🔹 Grupo de excepción


GRP_USB_EXCEPCIONES


Este grupo contiene únicamente los equipos que requieren acceso temporal a dispositivos USB.

---

### 🔹 GPO de excepción

**GPO:** `Excepcion USB Temporal`

Configuración:


Computer Configuration
└── Administrative Templates
└── System
└── Removable Storage Access
└── All Removable Storage classes: Allow


Filtrado de seguridad aplicado exclusivamente a:


GRP_USB_EXCEPCIONES


---

## 🔐 Principios de Seguridad Aplicados

Este modelo respeta:

- Principio de mínimo privilegio
- Control basado en roles (RBAC)
- Segregación de funciones
- Gestión controlada de excepciones
- Arquitectura escalable

---

## 📋 Gestión y Bitácora

Toda excepción debe registrarse formalmente incluyendo:

- Equipo afectado
- Usuario responsable
- Motivo
- Fecha de inicio
- Fecha de término
- Aprobador

Esto permite:

- Auditoría posterior
- Trazabilidad completa
- Reversibilidad inmediata
- Control operativo

---

## 🏛️ Justificación ante Auditoría

El uso de grupos de seguridad para gestionar excepciones permite mantener la integridad de las políticas base, evitando modificaciones directas en GPO globales que puedan comprometer la postura de seguridad organizacional.

Este modelo desacopla la política de la excepción, reduciendo riesgo operativo y permitiendo escalabilidad controlada.

---

## 🧩 Ventajas del Modelo

✔ No altera la GPO base  
✔ Permite segmentación granular  
✔ Es auditable  
✔ Es reversible  
✔ Escala a cientos de equipos  
✔ Facilita automatización futura  

---

## 🚀 Conclusión

La gestión de excepciones mediante grupos de seguridad permite mantener un bosque limpio, organizado y alineado con buenas prácticas de gobierno de acceso.

Este enfoque es aplicable a cualquier tipo de política (USB, CMD, Panel de Control, Firewall, etc.)