# Guía de Instalación y Configuración para el Subdirector de Servicios Informáticos

## Objetivo
Esta guía proporciona los pasos para instalar y configurar Hermes Agent como herramienta de apoyo operativo para el Subdirector de Servicios Informáticos de la UJMD, enfocada en la coordinación de equipos y supervisión de operaciones diarias.

## Requisitos Previos

- Sistema operativo: Linux (Ubuntu 20.04+/Debian 11+ recomendado), macOS, o WSL2 en Windows.
- Conexión a internet.
- Privilegios de sudo (para instalación de dependencias).
- Cuenta de GitHub con acceso al repositorio [hermes-agent-knowledge-base](https://github.com/untaldouglas/hermes-agent-knowledge-base).
- Credenciales de API para los proveedores de LLM deseados.

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
- **Modelo y Proveedor**: Seleccione su proveedor preferido.
- **Terminal**: Local por defecto.
- **Herramientas**: Active: `web`, `terminal`, `file`, `skills`, `memory`, `cronjob`, `delegation` (útil para coordinar tareas).
- **Gateway**: Opcional, según uso en plataformas de mensajería.
- **Memoria**: Active para aprendizaje persistente.
- **Credenciales**: Añada API keys necesarias.

### 4. Clonar el Repositorio de Conocimiento

```bash
git clone https://github.com/untaldouglas/hermes-agent-knowledge-base.git ~/.hermes/knowledge-base
```

### 5. Configurar Perfil de Subdirector

```bash
hermes profile create subdirector --clone-all
hermes profile use subdirector
```

### 6. Instalar Skills Específicas

```bash
hermes skills install ~/.hermes/knowledge-base/skills/erpnext-audit
hermes skills install ~/.hermes/knowledge-base/skills/coordinador-report
hermes skills install ~/.hermes/knowledge-base/skills/tecnico-report
hermes skills install ~/.hermes/knowledge-base/skills/onboarding-it
```

### 7. Configurar Trabajos Cron

Configure reportes y tareas automatizadas relevantes para su rol:

```bash
# Reporte diario de estado de equipos y técnicos
hermes cron create "0 18 * * *" --name "Reporte Diario de Operaciones" --prompt "Generar reporte diario de estado de equipos, tickets pendientes y actividades de técnicos" --skills tecnico-report,coordinador-report --deliver origin

# Reporte semanal de tendencias y métricas
hermes cron create "0 9 * * 1" --name "Reporte Semanal de Tendencias" --prompt "Analizar tendencias de incidencias, tiempo de respuesta y carga de trabajo semanal" --skills erpnext-audit --deliver origin

# Recordatorio de reuniones de seguimiento
hermes cron create "0 9 * * 1,3,5" --name "Recordatorio de Reuniones de Seguimiento" --prompt "Recordar reuniones de seguimiento de proyectos y mantenimiento" --deliver origin
```

### 8. Personalizar Memoria y Preferencias

```bash
hermes memory add --target user --content "Soy Subdirector de Servicios Informáticos en la UJMD, responsable de la coordinación de equipos técnicos y supervisión de operaciones diarias."
hermes memory add --target user --content "Prefiero comunicación en español latinoamericano, usando términos como empresa, computadora, celular, platicar, chévere, plata, trabajo, carro/auto."
hermes memory add --target user --content "Me enfoco en la eficiencia operativa, seguimiento de SLAs y mejora continua alineada con ITIL y LEAN."
```

### 9. Verificar la Configuración

```bash
hermes chat -q "¿Cuál es el estado actual de los tickets de alta prioridad en ERPNext?"
```

## Buenas Prácticas para el Subdirector

- **Delegación Eficaz**: Use la habilidad de delegación (`delegate_task`) para asignar tareas a técnicos y coordinadores mediante sesiones secundarias de Hermes.
- **Monitoreo de SLA**: Configure skills personalizadas para monitorear tiempos de respuesta y cumplimiento de acuerdos de nivel de servicio.
- **Reuniones Productivas**: Use Hermes para preparar agendas, tomar actas y seguir acciones de reuniones de equipo.
- **Capacitación Continua**: Comparta conocimientos y skills útiles con su equipo a través del repositorio de conocimiento.

## Seguridad y Confidencialidad

- Mantenga confidencial la información de personal y proyectos sensibles.
- Use perfiles separados para isolar datos de diferentes niveles de responsabilidad.
- Revise periódicamente los permisos de las skills activas.

---
*Documento mantenido por la Dirección de Servicios Informáticos - UJMD*