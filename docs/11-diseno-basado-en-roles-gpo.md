# Diseño de GPO Basado en Roles (RBAC)

## 📌 Descripción

Después de analizar:

- Herencia
- Precedencia
- Enforced
- Filtrado de seguridad

Se definió una estrategia de diseño basada en roles,
evitando depender del orden manual de las GPO.

Este enfoque permite escalar la infraestructura
de forma ordenada y mantenible.

---

## 🧠 Problema detectado

Depender del orden manual de vínculos de GPO:

- No escala en entornos grandes.
- Genera conflictos difíciles de diagnosticar.
- Obliga a modificar precedencias constantemente.
- Aumenta el riesgo de errores administrativos.

En una empresa con cientos de usuarios,
este enfoque no es sostenible.

---

## 🎯 Solución adoptada: RBAC

Se implementó un modelo basado en grupos de seguridad:


- GRP_TI
- GRP_CALLCENTER


Las GPO se aplican mediante:

- Vinculación a la OU correspondiente.
- Filtrado de seguridad por grupo.
🏗️ Arquitectura implementada


```
darkzone.cl
└── Darkzone
    ├── Usuarios
    ├── Equipos
    ├── Servidores
    └── Grupos
        ├── GRP_TI
        └── GRP_CALLCENTER
```

Las políticas se asignan según rol:

TI → Permitir CMD

Callcenter → Bloqueo CMD

Sin necesidad de:

Modificar orden manual de GPO.

Usar Enforced.

Bloquear herencia innecesariamente.

🔐 Ventajas del modelo

Escalable.

Fácil de mantener.

Reduce conflictos.

Permite cambios rápidos de cargo.

Minimiza errores administrativos.

Para cambiar permisos de un usuario:

Solo se modifica su pertenencia a grupo.

No es necesario moverlo de OU ni alterar precedencias.

🧠 Conclusión técnica

El diseño basado en roles (RBAC):

Se adapta mejor a entornos empresariales.

Reduce la complejidad operativa.

Evita el uso excesivo de GPO Exigidas.

Facilita auditorías y troubleshooting.

Este modelo permite que la infraestructura crezca
sin perder control administrativo.