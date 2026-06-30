# Base de Conocimiento de Hermes Agent para la Dirección de Informática - UJMD

Este repositorio contiene el conocimiento formalmente definido para implementar Hermes Agent como herramienta de apoyo para cada miembro de la Dirección de Informática de la Universidad José María Delgado (UJMD).

## Objetivo

Proporcionar un repositorio centralizado donde se documenten:

- Procedimientos operativos estándar (SOPs) para el uso de Hermes Agent.
- Guías de instalación y configuración por rol (Director, Subdirector, Coordinadores, Analistas, Asistentes, Administradores, Auxiliares Técnicos).
- Skills personalizadas desarrolladas para las necesidades específicas de la DSI.
- Plantillas de reportes, reportes cron, y flujos de trabajo automatizados.
- Buenas prácticas de gobernanza alineadas con ITIL, COBIT, PRINCE2 y LEAN.
- Ejemplos de uso práctico: auditorías ERPNext, reportes de técnicos/coordinadores, gestión de tickets, etc.

## Estructura del Repositorio

```
hermes-agent-knowledge-base/
├── README.md                 # Este archivo
├── docs/                     # Documentación detallada
│   ├── instalación/
│   │   ├── director.md
│   │   ├── subdirector.md
│   │   ├── coordinador.md
│   │   └── tecnico.md
│   ├── uso/
│   │   ├── agente-personal.md
│   │   ├── cron-jobs.md
│   │   └── habilidades-personalizadas.md
│   └── gobernanza/
│       ├── itil.md
        ├── cobit.md
        ├── prince2.md
        └── lean.md
├── skills/                   # Skills personalizadas de Hermes Agent
│   ├── erpnext-audit/        # Skill para auditoría ERPNext (ya existente)
│   ├── tecnico-report/       # Skill para generar reportes de técnicos
│   ├── coordinador-report/   # Skill para reportes de coordinadores
│   └── onboarding-it/        # Skill para onboarding de personal IT
├── templates/                # Plantillas de documentos, reportes, etc.
│   ├── reporte-tecnico.md
│   ├── reporte-coordinador.md
│   ├── agenda-reunion.md
│   └── acta-reunión.md
├── scripts/                  # Scripts auxiliares para automatización
│   ├── sync_gbrain.sh
│   ├── backup-personal.sh
│   └── generar-reporte.sh
├── cron/                     # Definiciones de trabajos cron (hermes cronjob)
│   ├── auditoria-diaria.json
│   ├── reporte-tecnicos-diario.json
│   └── reporte-coordinadores-semanal.json
└── .github/
    ├── ISSUE_TEMPLATE/
    └── PULL_REQUEST_TEMPLATE/
```

## Cómo Contribuir

1. Fork este repositorio.
2. Crea una rama para tu contribución: `git checkout -b feature/nombre-de-tu-feature`.
3. Agrega o modifica archivos en las carpetas apropiadas.
4. Haz commit con mensajes claros y convencionales.
5. Abre un Pull Request describiendo los cambios y su beneficio para la DSI.

## Directrices de Estilo

- Usar español latinoamericano (términos preferidos: empresa, computadora, celular, platicar, chévere, plata, trabajo, carro/auto).
- Mantener un tono ejecutivo, claro y alineado con marcos de gobernanza (ITIL, COBIT, PRINCE2, LEAN).
- Evitar divulgar información personal identificable (PII) sin autorización.
- Documentar supuestos, dependencias y pasos de verificación.

## Próximos Pasos

1. Poblar la documentación inicial basada en la carpeta existente "Carpeta administrativa del personal de la Dirección de Informática vigente-20260615T150917Z-3-001".
2. Crear skills personalizadas para los reportes diarios de técnicos y coordinadores (ya existente en cron diario a las 18:00).
3. Establecer un proceso de revisión y aprobación de documentos dentro del equipo de gobernanza de la DSI.
4. Capacitar al personal usando este repositorio como referencia.

## Licencia

Este repositorio está bajo la Licencia MIT - ver archivo LICENSE para detalles.

---

*Desarrollado para la Dirección de Informática de la UJMD por Hermes Agent (Nous Research).*