# Guía de Instalación y Configuración para Analistas Programadores y Asistentes Técnicos

## Objetivo
Esta guía proporciona los pasos para instalar y configurar Hermes Agent como herramienta de apoyo para Analistas Programadores, Asistentes Técnicos y roles afines en la UJMD, enfocada en el desarrollo, mantenimiento de sistemas y soporte técnico diario.

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
- **Terminal**: Local por defecto (útil para ejecutar comandos de desarrollo).
- **Herramientas**: Active: `web`, `terminal`, `file`, `skills`, `memory`, `cronjob`, `code_execution` (útil para probar scripts), `vision` (si necesita analizar imágenes o documentos).
- **Gateway**: Opcional.
- **Memoria**: Active para aprendizaje persistente.
- **Credenciales**: Añada API keys necesarias.

### 4. Clonar el Repositorio de Conocimiento

```bash
git clone https://github.com/untaldouglas/hermes-agent-knowledge-base.git ~/.hermes/knowledge-base
```

### 5. Configurar Perfil de Técnico

```bash
hermes profile create tecnico --clone-all
hermes profile use tecnico
```

### 6. Instalar Skills Específicas

```bash
hermes skills install ~/.hermes/knowledge-base/skills/erpnext-audit
hermes skills install ~/.hermes/knowledge-base/skills/tecnico-report
hermes skills install ~/.hermes/knowledge-base/skills/onboarding-it
# Si desarrolla o mantiene sistemas específicos:
# hermes skills install <skill-name>
```

### 7. Configurar Trabajos Cron

Configure tareas automatizadas relevantes para su rol:

```bash
# Reporte diario de actividades técnicas
hermes cron create "0 18 * * *" --name "Reporte Diario de Actividades" --prompt "Generar reporte de tareas completadas, tiempo dedicado a cada proyecto, incidencias resueltas y pendientes" --skills tecnico-report --deliver origin

# Recordatorio de reuniones de seguimiento
hermes cron create "0 9 * * 1,3,5" --name "Recordatorio de Reuniones de Seguimiento" --prompt "Recordar reuniones de seguimiento de tareas y preparación de avances" --deliver origin

# Escaneo semanal de actualizaciones de seguridad (opcional)
hermes cron create "0 2 * * 0" --name "Escaneo Semanal de Seguridad" --prompt "Buscar actualizaciones de seguridad para sistemas críticos y generar reporte" --skills web --deliver origin
```

### 8. Personalizar Memoria y Preferencias

```bash
hermes memory add --target user --content "Soy Analista Programador/Asistente Técnico en la UJMD, responsable del desarrollo, mantenimiento y soporte de sistemas informáticos."
hermes memory add --target user --content "Prefiero comunicación en español latinoamericano, usando términos como empresa, computadora, celular, platicar, chévere, plata, trabajo, carro/auto."
hermes memory add --target user --content "Me enfoco en la calidad del código, documentación clara y resolución eficiente de incidencias."
```

### 9. Verificar la Configuración

```bash
hermes chat -q "¿Cuáles son las incidencias técnicas pendientes de hoy según el último reporte?"
```

## Buenas Prácticas para Técnicos

- **Desarrollo y Mantenimiento**: Use la herramienta `terminal` para ejecutar comandos de desarrollo, `file` para editar configuraciones, y `code_execution` para probar fragmentos de código.
- **Documentación**: Use habilidades para generar documentación técnica y mantener wikis actualizadas.
- **Soporte Técnico**: Configure skills para crear tickets en ERPNext, buscar soluciones en bases de conocimiento y comunicar avances a usuarios.
- **Aprendizaje Continuo**: Use Hermes para investigar nuevas tecnologías, leer documentación y compartir conocimientos con el equipo.

## Seguridad y Confidencialidad

- Proteja credenciales de acceso a sistemas y repositorios.
- No comparta información sensible de configuración o código fuente sin autorización.
- Use perfiles separados si trabaja en proyectos con diferentes niveles de confidencialidad.
- Revise periódicamente los permisos de las skills y herramientas activas.

---
*Documento mantenido por la Dirección de Servicios Informáticos - UJMD*