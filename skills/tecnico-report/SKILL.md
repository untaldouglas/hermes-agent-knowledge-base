# Skill para Generar Reportes de Técnicos

## Objetivo
Esta skill proporciona funcionalidades para generar reportes diarios de actividades de técnicos, incluyendo incidencias resueltas, tareas pendientes y tiempo dedicado a cada proyecto.

## Operaciones

### generar_reporte_diario
Genera un reporte diario de actividades para un técnico específico.

```bash
/skill tecnico-report generar_reporte_diario --tecnico "Nombre del Técnico" --fecha "YYYY-MM-DD"
```

### listar_incidencias_resueltas
Lista las incidencias resueltas por un técnico en un período determinado.

```bash
/skill tecnico-report listar_incidencias_resueltas --tecnico "Nombre del Técnico" --dias 7
```

### listar_tareas_pendientes
Muestra las tareas pendientes asignadas a un técnico.

```bash
/skill tecnico-report listar_tareas_pendientes --tecnico "Nombre del Técnico"
```

### registrar_actividad
Registra una actividad realizada por un técnico para seguimiento posterior.

```bash
/skill tecnico-report registrar_actividad --tecnico "Nombre del Técnico" --actividad "Descripción de la actividad" --horas 2.5
```

## Implementación
Esta skill utiliza las herramientas `memory`, `session_search`, `todo` y `file` para almacenar y recuperar información de actividades.

## Flujo de Trabajo Sugerido
1. Al comenzar el día, registrar las tareas planificadas usando `/todo add`
2. Durante el día, registrar actividades completadas usando `registrar_actividad`
3. Al final del día, generar el reporte diario con `generar_reporte_diario`
4. Revisar incidencias resueltas y tareas pendientes para planificar el día siguiente

## Ejemplo de Uso
```bash
# Registrar actividades durante el día
/skill tecnico-report registrar_actividad --tecnico "Juan Pérez" --actividad "Resolución de incidente #INC00123 - Impresora no responde" --horas 1.5
/skill tecnico-report registrar_actividad --tecnico "Juan Pérez" --actividad "Mantenimiento preventivo de servidores de archivo" --horas 2.0

# Generar reporte al final del día
/skill tecnico-report generar_reporte_diario --tecnico "Juan Pérez" --fecha "2026-06-30"

# Revisar tareas pendientes
/skill tecnico-report listar_tareas_pendientes --tecnico "Juan Pérez"
```

## Notas
- Esta skill está diseñada para integrarse con el skill `erpnext-audit` para obtener datos reales de incidencias del sistema ERPNext.
- Los datos se almacenan en la memoria persistente de Hermes para permitir el seguimiento histórico.
- Se puede configurar un trabajo cron diario para generar automáticamente estos reportes para todos los técnicos.