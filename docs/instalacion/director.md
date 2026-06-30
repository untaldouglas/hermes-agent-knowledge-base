# Guía de Instalación y Configuración para el Director de Servicios Informáticos

## Objetivo
Esta guía proporciona los pasos para instalar y configurar Hermes Agent como herramienta de apoyo estratégico para el Director de Servicios Informáticos de la UJMD, alineada con los marcos de gobierno ITIL, COBIT, PRINCE2 y LEAN.

## Requisitos Previos

- Sistema operativo: Linux (Ubuntu 20.04+/Debian 11+ recomendado), macOS, o WSL2 en Windows.
- Conexión a internet.
- Privilegios de sudo (para instalación de dependencias).
- Cuenta de GitHub con acceso al repositorio [hermes-agent-knowledge-base](https://github.com/untaldouglas/hermes-agent-knowledge-base).
- Credenciales de API para los proveedores de LLM deseados (OpenRouter, Anthropic, OpenAI, etc.) - opcional para inicio rápido con modelos locales.

## Pasos de Instalación

### 1. Instalar Hermes Agent

Ejecute el script de instalación oficial:

```bash
curl -fsSL https://hermes-agent.nousresearch.com/install.sh | bash
```

Esto instalará Hermes en `~/.hermes/` y agregará el comando `hermes` a su PATH.

### 2. Verificar la instalación

```bash
hermes doctor
```

Este comando verifica dependencias y configuración. Resuelva cualquier asunto reportado antes de continuar.

### 3. Configuración inicial

Ejecute el asistente de configuración interactiva:

```bash
hermes setup
```

Siga las indicaciones para configurar:

- **Modelo y Proveedor**: Seleccione su proveedor preferido (ej. OpenRouter para acceso a múltiples modelos, o Anthropic para Claude). Se recomienda comenzar con un modelo gratuito disponible en OpenRouter para pruebas.
- **Terminal**: Deje el valor por defecto (local) a menos que necesite entornos aislados (docker, ssh, modal).
- **Herramientas**: Active al menos: `web`, `terminal`, `file`, `skills`, `memory`, `cronjob`. Puede habilitar más según sus necesidades (vision, image_gen, etc.).
- **Gateway**: Configure si desea usar Hermes en plataformas de mensajería (Telegram, Discord, etc.). Para uso inicial en terminal, puede omitirlo.
- **Memoria**: Active la memoria persistente para que Hermes aprenda de sus interacciones.
- **Credenciales**: Añada las API keys de los proveedores seleccionados mediante `hermes auth add <provider>`.

### 4. Clonar el Repositorio de Conocimiento

```bash
git clone https://github.com/untaldouglas/hermes-agent-knowledge-base.git ~/.hermes/knowledge-base
```

Esto hará disponible la documentación, skills, plantillas y scripts localmente.

### 5. Configurar Perfil de Director

Cree un perfil específico para su rol para mantener aisladas sus configuraciones, skills y memoria:

```bash
hermes profile create director --clone-all
hermes profile use director
```

Esto clonará todas las skills, plugins, cron jobs y memoria del perfil predeterminado al nuevo perfil "director".

### 6. Instalar Skills Específicas de la DSI

Desde el repositorio clonado, instale las skills personalizadas:

```bash
hermes skills install ~/.hermes/home/dagalindo/hermes-agent-knowledge-base/skills/erpnext-audit
hermes skills install ~/.hermes/hermes-agent-knowledge-base/skills/tecnico-report
hermes skills install ~/.hermes/hermes-agent-knowledge-base/skills/coordinador-report
hermes skills install ~/.hermes/hermes-agent-knowledge-base/skills/onboarding-it
```

Verifique las skills instaladas:

```bash
hermes skills list
```

### 7. Configurar Trabajos Cron (Cron Jobs)

Configure los trabajos cron automatizados para reportes diarios y semanales:

```bash
hermes cron create "0 18 * * *" --name "Auditoría Diaria ERPNext" --prompt "Ejecutar auditoría ERPNext y generar reporte de incidencias y estado de tickets" --skills erpnext-audit --deliver origin
hermes cron create "0 18 * * 1" --name "Reporte Semanal de Coordinadores" --prompt "Generar reporte semanal de actividades de coordinadores y técnicos" --skills coordinador-report --deliver origin
hermes cron create "0 7 * * *" --name "Reporte Diario de Técnicos" --prompt "Generar reporte diario de actividades de técnicos y estado de incidencias" --skills tecnico-report --deliver origin
```

Verifique los trabajos creados:

```bash
hermes cron list
```

### 8. Personalizar la Memoria y Preferencias

Agregue sus preferencias de comunicación y datos de perfil utilizando la herramienta de memoria:

```bash
hermes memory add --target user --content "Prefiero comunicación en español latinoamericano, usando términos como empresa, computadora, celular, platicar, chévere, plata, trabajo, carro/auto."
hermes memory add --target user --content "Soy Director de Servicios Informáticos en la UJMD con 35+ años de experiencia, coordinando 18 equipos, sirviendo a 5000+ estudiantes, 800 profesores y 600 staff."
hermes memory add --target user --content "Sigo marcos de gobierno: ITIL, COBIT, PRINCE2, LEAN. Priorizo seguridad de datos y soluciones escalables."
```

### 9. Verificar la Configuración Final

Ejecute una consulta de prueba para asegurarse de que todo funciona:

```bash
hermes chat -q "¿Cuál es el estado actual de las incidencias en ERPNext según el último reporte?"
```

Debería obtener una respuesta basada en las skills y datos configurados.

## Buenas Prácticas de Gobernanza

- **ITIL**: Use Hermes para gestionar incidentes, problemas y cambios mediante habilidades específicas y documentación estandarizada.
- **COBIT**: Alinee el uso de Hermes con los dominios de gobernanza y gestión de TI. Documente políticas de uso en el repositorio.
- **PRINCE2**: Utilice Hermes para apoyar la gestión de proyectos, creando skills para seguimiento de hitos y riesgos.
- **LEAN**: Elimine el desperdicio en procesos de TI automatizando reportes y tareas repetitivas con cron jobs y skills.

## Seguridad y Confidencialidad

- No comparta información personal identificable (PII) sin autorización.
- Use el perfil de Director para isolar datos sensibles de otros usuarios.
- Revise periódicamente los permisos de las skills y herramientas activas.
- Habilite la redacción de secretos en la configuración: `hermes config set security.redact_secrets true`.

## Soporte y Mantenimiento

- Participe en las reuniones mensuales de la DSI para compartir experiencias y mejores prácticas con Hermes.
- Contribuya al repositorio de conocimiento mejorando la documentación, creando nuevas skills o reportando problemas.
- Mantenga Hermes actualizado: `hermes update`.

## Contacto

Para soporte técnico o consultas sobre la implementación, contacte al equipo de Servicios Informáticos o consulte la documentación en este repositorio.

---
*Documento mantenido por la Dirección de Servicios Informáticos - UJMD*