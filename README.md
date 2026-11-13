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

Pegar la URL de este repo en un chat no instala la skill. Hay que instalarla según dónde uses Claude.

**Claude Code.** Copia la carpeta de la skill a tu directorio de skills:

```bash
git clone https://github.com/DMansOS/sie7e-skill-elementor
cp -r sie7e-skill-elementor/sie7e-diseno-web-elementor ~/.claude/skills/
```

**claude.ai (web o app).** Las skills se suben como archivo ZIP:

1. Descarga o clona el repo.
2. Comprime la carpeta `sie7e-diseno-web-elementor` en un ZIP (la carpeta debe contener `SKILL.md`).
3. Ve a Ajustes → Capacidades → Skills → Subir skill y selecciona el ZIP.
4. Activa la skill.

**CSS del kit.** Pega el contenido de `sie7e-kit-base.css` en Elementor → Ajustes del sitio → CSS personalizado de tu WordPress maestro. Los valores de `:root` se ajustan por cliente.

## Adáptala a tu caso

La skill refleja un flujo de trabajo concreto y no funcionará igual sin cambios. Antes de usarla, revisa y sustituye por lo tuyo:

- **Ficha de proyecto en Notion:** usa una base de datos "Proyectos Web" con propiedades concretas. Necesitas Notion conectado y esa base creada, o quitar esa parte.
- **Kit de plugins:** JetSmartFilters, JetEngine, ElementsKit Pro, Rank Math, LiteSpeed Cache, Wordfence, WP Mail SMTP, All-in-One WP Migration y otros. Cambia la lista por la tuya.
- **Kit base en .wpress:** la skill asume que clonas cada web desde un WordPress maestro exportado con All-in-One WP Migration.
- **Convenciones propias:** prefijos de clases CSS (`c-`, `u-`, `woo-`), nombres de plantillas y rondas de cambios con el cliente.
- **Tipos de artifact de Claude:** Design y Design System para maquetas y guía de estilo. Si tu cuenta no los tiene, sustitúyelos por otro método.
- **Páginas legales:** las de Panamá y Venezuela son las del autor. Son un punto de partida y deben revisarse con un abogado de cada país.
- **Contexto del usuario:** la sección inicial describe al autor (idioma, tipo de proyectos, forma de trabajar). Reescríbela para ti.

## Licencia

MIT. Consulta el archivo `LICENSE`.
