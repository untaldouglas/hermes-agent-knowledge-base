# Guía de Instalación y Configuración para Coordinadores de Equipos Técnicos

## Objetivo
Esta guía proporciona los pasos para instalar y configurar Hermes Agent como herramienta de apoyo para Coordinadores de Equipos Técnicos en la UJMD, enfocada en la gestión de equipos, asignación de tareas y seguimiento de proyectos.

## Requisitos Previos

- Sistema operativo: Linux (Ubuntu 20.04+/Debian 11+ recomendado), macOS, o WSL2 en Windows.
- Conexión a internet.
- Privilegios de usuario (no se requiere sudo para instalación en el directorio home).
- Cuenta de GitHub con acceso al repositorio [hermes-agent-knowledge-base](https://github.com/untaldouglas/hermes-agent-knowledge-base).

## Pasos de Instalación

### 1. Instalar Hermes Agent

```bash
curl -fsSL https://hermes-agent.nousresearch.com/install.sh | bash
```

### 2. Verificar la instalación

```bash
hermes doctor
```

### 3. Configuración inicial

Ejecute el asistente de configuración interactiva:

```bash
hermes setup
```

Configure según sus necesidades:
- **Modelo y Proveedor**: Seleccione su proveedor preferido (OpenRouter, Anthropic, etc.)
- **Terminal**: Local por defecto.
- **Herramientas**: Active: `web`, `terminal`, `file`, `skills`, `memory`, `cronjob`, `delegation` (útil para delegar tareas a técnicos).
- **Gateway**: Opcional.
- **Memoria**: Active para aprendizaje persistente.
- **Credenciales**: Añada API keys necesarias.

### 4. Clonar el Repositorio de Conocimiento

```bash
git clone https://github.com/untaldouglas/hermes-agent-knowledge-base.git ~/.hermes/knowledge-base
```

### 5. Configurar Perfil de Coordinador

```bash
hermes profile create coordinador --clone-all
hermes profile use coordinador
```

### 6. Instalar Skills Específicas

```bash
hermes skills install ~/.hermes/knowledge-base/skills/erpnext-audit
hermes skills install ~/.hermes/knowledge-base/skills/coordinador-report
hermes skills install ~/.hermes/knowledge-base/skills/tecnico-report
hermes skills install ~/.hermes/knowledge-base/skills/onboarding-it
```

### 7. Configurar Trabajos Cron

Configure tareas automatizadas relevantes para su rol:

```bash
# Reporte diario de estado del equipo y tareas pendientes
hermes cron create "0 17 * * *" --name "Reporte Diario del Equipo" --prompt "Generar reporte de actividades del día, tareas completadas, pendientes y bloqueos" --skills coordinador-report --deliver origin

# Reporte semanal de avances de proyectos
hermes cron create "0 9 * * 1" --name "Reporte Semanal de Proyectos" --prompt "Resumir avances de proyectos, riesgos identificados y próximos hitos" --skills coordinador-report --deliver origin

# Recordatorio de reuniones de equipo
hermes cron create "0 9 * * 1,3,5" --name "Recordatorio de Reuniones de Equipo" --prompt "Recordar reuniones de seguimiento de equipo y preparación de agenda" --deliver origin
```

### 8. Personalizar Memoria y Preferencias

```bash
hermes memory add --target user --content "Soy Coordinador de Equipos Técnicos en la UJMD, responsable de la asignación de tareas, seguimiento de proyectos y soporte técnico."
hermes memory add --target user --content "Prefiero comunicación en español latinoamericano, usando términos como empresa, computadora, celular, platicar, chévere, plata, trabajo, carro/auto."
hermes memory add --target user --content "Me enfoco en la eficiencia del equipo, claridad en la comunicación y seguimiento de indicadores de desempeño."
```

### 9. Verificar la Configuración

```bash
hermes chat -q "¿Cuál es el estado actual de las tareas asignadas a mi equipo para hoy?"
```

## Buenas Prácticas para Coordinadores

- **Gestión de Tareas**: Use la habilidad de delegación para asignar tareas específicas a técnicos y seguir su progreso.
- **Informes Periódicos**: Configure reportes automáticos para mantener informados a superiores y al equipo.
- **Reuniones Efectivas**: Use Hermes para preparar actas, seguir acciones y documentar decisiones.
- **Capacitación del Equipo**: Comparta skills y conocimientos útiles con su equipo a través del repositorio.

## Seguridad y Confidencialidad

- Proteja la información de proyectos y asignaciones de personal.
- Use perfiles separados si maneja información sensible de diferentes equipos.
- Revise periódicamente los permisos de las skills activas.

---
*Documento mantenido por la Dirección de Servicios Informáticos - UJMD*