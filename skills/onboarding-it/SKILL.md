# Skill para Onboarding de Personal de TI

## Descripción
Esta skill proporciona un proceso de onboarding para nuevos miembros de la Dirección de Informática, siguiendo las directrices de ITIL, LEAN, Flow framework y PRINCE2. Facilita la creación de una base de conocimiento de SOPs y FAQs, gestión de tareas y flujos de trabajo, automatización mediante trabajos cron, delegación de tareas y recuperación de interacciones pasadas.

## Requisitos Previos
- Hermes Agent instalado y en ejecución.
- Conocimiento básico de la CLI de Hermes (`hermes config`, `hermes tools`, `hermes skills`, `hermes cron`).
- Acceso a la terminal y capacidad para editar archivos.

## Operaciones

### configurar_conocimiento_base
Configura una habilidad de base de conocimiento para almacenar y recuperar SOPs y FAQs.

```bash
/skill onboarding-it configurar_conocimiento_base
```

### configurar_gestion_tareas
Configura la gestión de tareas usando las herramientas `todo` y `delegation`.

```bash
/skill onboarding-it configurar_gestion_tareas
```

### configurar_automatizacion_cron
Configura trabajos cron recurrentes para métricas de flujo y actualización de la base de conocimiento.

```bash
/skill onboarding-it configurar_automatizacion_cron
```

### configurar_delegacion_planificacion
Configura la delegación de tareas y planificación usando las herramientas de delegación y planificación.

```bash
/skill onboarding-it configurar_delegacion_planificacion
```

### configurar_recuperacion_interacciones
Configura la recuperación de interacciones pasadas usando la herramienta `session_search`.

```bash
/skill onboarding-it configurar_recuperacion_interacciones
```

## Implementación
Esta skill utiliza las herramientas `memory`, `session_search`, `delegation`, `cronjob`, `todo`, `clarify`, `web` y `vision`.

## Flujo de Trabajo Sugerido
1. **Configurar la base de conocimiento** para almacenar SOPs y FAQs.
2. **Configurar la gestión de tareas** para planificar y seguir el trabajo diario.
3. **Configurar la automatización con cron** para generar reportes semanales de métricas y actualizar la base de conocimiento.
4. **Configurar la delegación** para asignar tareas a subagentes cuando sea necesario.
5. **Configurar la recuperación de interacciones** para revisar trabajo anterior y evitar duplicar esfuerzo.

## Ejemplo de Uso
```bash
# Configurar la base de conocimiento
/skill onboarding-it configurar_conocimiento_base

# Añadir un SOP de ejemplo
/skill it-kb add "Procedimiento para restablecer contraseñas de usuarios" --type SOP --category Seguridad --tags password,reset,usuarios

# Configurar gestión de tareas
/skill onboarding-it configurar_gestion_tareas

# Añadir tareas del día
/todo add "Revisar incidentes del día anterior" --priority alta
/todo add "Actualizar KB con solución de incidente #123" --category KB

# Configurar automatización cron
/skill onboarding-it configurar_automatizacion_cron

# Ver trabajos cron creados
hermes cron list
```

## Notas
- Esta skill está diseñada para ser adaptable a diferentes roles dentro de la Dirección de Informática (Director, Subdirector, Coordinadores, Técnicos).
- Se recomienda revisar y actualizar periódicamente la base de conocimiento y los trabajos cron según las necesidades evolutivas del departamento.