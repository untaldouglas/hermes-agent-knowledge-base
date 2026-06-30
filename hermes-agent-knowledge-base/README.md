# Base de Conocimiento de Hermes Agent para la Dirección de Informática - UJMD

Este repositorio contiene el conocimiento formalmente definido para implementar Hermes Agent como herramienta de apoyo para cada uno de los miembros de la Dirección de Informática de la Universidad José María Delgado (UJMD).

Este repositorio contiene el conocimiento formalmente definido para implementar Hermes Agent como herramienta de apoyo para cada miembro de la Dirección de Informática de apoyo para cada miembro de la Dirección de Informática de la Universidad José María Delgado (UJMD), alineado con los marcos de gobierno ITIL, COBIT, PRINCE2 y LEAN.

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
│       ├── cobit.md
│       ├── prince2.md
│       └── lean.md
├── skills/                   # Skills personalizadas de Hermes Agent
│   ├── erpnext-audit/        # Skill para auditoría ERPNext (existente en el hub)
│   ├── tecnico-report/       # Skill para generar reportes de técnicos
│   ├── coordinador-report/   # Skill para generar reportes de coordinadores
│   └── onboarding-it/        # Skill para onboarding de personal de TI
├── templates/                # Plantillas de documentos, reportes, etc.
│   ├── reporte-tecnico.md
│   ├── reporte-coordinador.md
│   ├── agenda-reunion.md
│   └── acta-reunión.md
├── scripts/│   ├── sync_gbrain.sh
│   ├── backup-personal.sh
│   └── generar-reporte.sh
├── cron/                     # Definiciones de trabajos cron (hermes cronjob)
│   ├── auditoria-diaria.json
│   ├── reporte-tecnicos-diario.json
│   └── reporte-coordinadores-semanal.json
├── externals/                # Recursos externos como submódulos Git
│   └── Implementar-AI-Fluentcy/  # Submódulo: Fluidez en IA para equipos técnicos
└── .github/
    ├── ISSUE_TEMPLATE/
    └── PULL_REQUEST_TEMPLATE/
```

## Recursos Externos Integrados

Este repositorio incluye como submódulo el proyecto [Implementar-AI-Fluentcy](https://github.com/untaldouglas/Implementar-AI-Fluentcy), ubicado en `externals/Implementar-AI-Fluentcy/`. Este recurso proporciona:

- **Marco de Fluidez en IA**: Guías para desarrollar competencias en inteligencia artificial aplicada al trabajo técnico y de gestión.
- **Plan Piloto**: Estrategia para introducir capacitación en IA en equipos de TI.
- **Playbook de Implementación**: Pasos prácticos para adoptar herramientas de IA en flujos de trabajo existentes.
- **Guías de Comunicación**: Plantillas y mejores prácticas para comunicar iniciativas de IA dentro de la organización.
- **Herramientas Recomendadas**: Lista de herramientas de IA evaluadas y su aplicabilidad en contextos de servicios de TI.
- **Blog y Casos de Uso**: Artículos y ejemplos de cómo la IA puede mejorar procesos como gestión de incidencias, automatización de reportes y capacitación continua.
- **Dashboards**: Ejemplos de tableros para monitorear la adopción y el impacto de las iniciativas de IA.

### Cómo utilizar el submódulo

Para inicializar y actualizar el submódulo después de clonar este repositorio:

```bash
git submodule update --init --recursive
```

Para obtener actualizaciones del repositorio externo:

```bash
cd externals/Implementar-AI-Fluentcy
git pull origin main
cd ..
git add externals/Implementar-AI-Fluentcy
git commit -m "Update externals/Implementar-AI-Fluentcy to latest commit"
```

## Cómo Contribuir

1. Fork este repositorio.
2. Crea una rama para tu contribución: `git checkout -b feature/nombre-de-tu-feature`.
3. Realiza tus cambios en las carpetas apropiadas (docs/, skills/, templates/, etc.).
4. Haz commit con un mensaje descriptivo.
5. Sube tu rama: `git push origin feature/nombre-de-tu-feature`.
6. Abre un Pull Request describiendo los cambios y su beneficio para la DSI.

## Licencia

Este repositorio está bajo la Licencia MIT - ver el archivo [LICENSE](LICENSE) para más detalles.

---

*Desarrollado para la Dirección de Informática de la UJMD con el apoyo de Hermes Agent (Nous Research).*