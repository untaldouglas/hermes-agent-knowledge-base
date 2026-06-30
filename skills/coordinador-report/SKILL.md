# Skill para Generar Reportes de Coordinadores

## Descripción
Esta skill permite generar reportes periódicos de actividades de coordinadores, incluyendo seguimiento de proyectos, estado de equipos y indicadores de desempeño.

## Operaciones

### generar_reporte_semanal
Genera un reporte semanal de actividades del coordinador.

```bash
/skill coordinador-report generar_reporte_semanal
```

### generar_reporte_proyecto
Genera un reporte enfocado en el estado de un proyecto específico.

```bash
/skill coordinador-report generar_reporte_proyecto --nombre "Nombre del Proyecto"
```

### listar_bloqueos
Lista los bloqueos o impedimentos identificados por el equipo.

```bash
/skill coordinador-report listar_bloqueos
```

## Implementación
Esta skill utiliza las herramientas `session_search`, `memory`, `todo` y `delegation` para recopilar y presentar la información.

## Ejemplo de Salida
```
# Reporte Semanal de Coordinador
Semana: 27 de junio de 2026

## Proyectos Activos
- Proyecto ERP: Fase de testing completada al 80%
- Proyecto Infraestructura: Migración a servidores cloud en progreso

## Métricas de Equipo
- Tickets resueltos: 45
- Tiempo promedio de respuesta: 4.2 horas
- Tasa de satisfacción: 4.5/5

## Bloqueos Identificados
- Falta de licencias para software X (pendiente aprobación presupuestal)
- Dependencia de equipo de redes para actualización de firewalls

## Próximos Pasos
- Reunión de seguimiento con equipo de desarrollo
- Preparar solicitud de licencias para próxima semana
```