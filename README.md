# sie7e-skill-elementor

Skill de Claude con una metodología para diseñar y construir webs de clientes (corporativas o WooCommerce) en WordPress con Elementor Pro: editables, con estilo propio y sin la estética genérica de las webs hechas con IA.

## Qué incluye

- `sie7e-diseno-web-elementor/SKILL.md`: la skill.
- `sie7e-diseno-web-elementor/sie7e-kit-base.css`: capa de CSS del kit base (variables de movimiento, foco visible, hovers solo con ratón, entradas con scroll y respeto a "reducir movimiento").

## Qué cubre la skill

- Tres tipos de encargo: web nueva, rediseño de una web existente y cambios puntuales.
- Flujo por etapas con dos aprobaciones del cliente: entrada, propuesta, producción, revisión y cierre.
- Dirección visual: tokens de color, tipografía, forma, espaciado y movimiento, con un nivel de atrevimiento del 1 al 5.
- Lista de señales de diseño hecho por IA y cómo corregirlas.
- Traducción de las maquetas a Elementor con widgets nativos y los globales del sitio.
- Reglas específicas de WooCommerce, copy, SEO y páginas legales por país.
- Checklist final de entrega.

## Instalación

En Claude Code, copia la carpeta de la skill a tu directorio de skills:

```bash
git clone https://github.com/DMansOS/sie7e-skill-elementor
cp -r sie7e-skill-elementor/sie7e-diseno-web-elementor ~/.claude/skills/
```

Para el CSS, pega el contenido de `sie7e-kit-base.css` en Elementor → Ajustes del sitio → CSS personalizado de tu WordPress maestro. Los valores de `:root` se ajustan por cliente.

## Adáptala a tu caso

La skill refleja un flujo de trabajo concreto: el kit de plugins, las convenciones de clases CSS, la ficha de proyecto en Notion y las páginas legales de Panamá y Venezuela son los del autor. Cámbialos por los tuyos antes de usarla. Las páginas legales son un punto de partida y deben revisarse con un abogado de cada país.

## Licencia

MIT. Consulta el archivo `LICENSE`.
