---
name: "sie7e-diseno-web-elementor"
description: "Metodología para diseñar y construir webs de clientes (corporativas o WooCommerce) en WordPress con Elementor Pro, editables y con estilo propio, no genérico."
---

# Diseño web con Elementor Pro: metodología

Usa esta skill cuando el usuario empiece o continúe un proyecto web para un cliente en WordPress + Elementor Pro, ya sea corporativo/informativo o tienda WooCommerce.

## Contexto del usuario
- Hace webs para clientes y las mantiene él mismo a largo plazo.
- Usa Elementor Pro. Prefiere construir de forma visual, pero sabe CSS.
- Dos tipos de proyecto: webs corporativas informativas y ecommerce WooCommerce, casi siempre con catálogos pequeños (decenas de productos).
- Quiere que Claude ayude a planificar Y a construir.
- Responde siempre en español.
- Todas sus skills llevan el prefijo `sie7e-` en el nombre.

## Principios no negociables
1. **Todo editable visualmente.** Widgets nativos y contenedores (flex/grid). El widget HTML y el CSS pesado solo como excepción justificada.
2. **Todo pasa por los globales.** Colores, fuentes y estilos de botones/formularios se definen en Ajustes del sitio y se referencian; nunca valores sueltos.
3. **Estructura reutilizable, estilo propio por cliente.** El kit base se repite; la dirección visual nunca.
4. **Nada de estética genérica de IA.** Cada diseño se contrasta con la sección "Señales de diseño hecho por IA" (más abajo) en dos momentos: al terminar las maquetas y antes de entregar la web. Si una señal aparece sin una razón del brief, se corrige.
5. **Lo que se aprueba es lo que se construye.** Las maquetas respetan lo que Elementor hace de forma nativa.
6. **Pensar en el mantenimiento.** Mismas convenciones en todos los sitios, pocos plugins, nada que se rompa con actualizaciones.
7. **Mínima intervención del usuario.** Claude encadena el trabajo solo y se detiene únicamente en las dos aprobaciones, cuando necesita un acceso o cuando falta un dato que no puede deducir. Las preguntas se agrupan en un solo mensaje y nunca se repite una ya respondida. Los entregables intermedios (fichas de análisis, fichas de construcción, moodboard) son internos: solo se muestran si piden una decisión o si el usuario construye esa parte él mismo.

## Kit base del usuario
- Tema: Hello Elementor con tema hijo (creado con Child Theme Configurator). Header, footer y plantillas se hacen con el Theme Builder de Elementor Pro. El código propio (PHP) va en el tema hijo, nunca en el tema padre.
- Plugins habituales:
  - JetSmartFilters: filtros de productos y listados.
  - JetEngine: solo cuando el proyecto necesita campos personalizados, tipos de contenido propios (CPT) o listados dinámicos. Si basta con lo nativo de WordPress/WooCommerce y Elementor Pro, no se instala.
  - ElementsKit Pro: widgets y opciones de diseño adicionales. Orden de preferencia: primero Elementor Pro nativo; ElementsKit solo cuando aporta algo que Elementor Pro no resuelve bien. Desactivar en su panel los widgets y módulos que no se usen (rendimiento) y estilizar sus widgets con los globales del sitio. En las fichas de construcción, indicar cuándo un elemento usa ElementsKit.
  - SEO: Rank Math.
  - Rendimiento: LiteSpeed Cache.
  - Seguridad: Wordfence.
  - Correo: WP Mail SMTP (formularios y correos de WooCommerce).
  - Antispam: Akismet, solo cuando hay blog con comentarios. Revisar que el plan de Akismet corresponda al uso (el gratuito es para sitios personales). Los formularios de Elementor se protegen con honeypot o reCAPTCHA.
  - Copias de seguridad y migración: All-in-One WP Migration and Backup + Unlimited Extension. Sirve para respaldos, para clonar el kit base en cada cliente (archivo .wpress) y para pasar de staging a producción. Las copias deben guardarse también fuera del servidor (descargadas o en la nube); si solo quedan en el mismo hosting no protegen ante una caída del servidor.
  - Gestión y entrega al cliente: White Label CMS (panel con la marca del usuario), Admin Notices Manager (panel limpio de avisos), FileBird Lite (carpetas en medios), Duplicate Page (duplicar páginas y plantillas), Child Theme Configurator.
- No añadir plugins fuera de esta lista sin justificarlo; si una función se resuelve con Elementor Pro o un plugin del kit, no se instala otro.
- Convención de clases CSS (en Avanzado → Clases CSS), en español o inglés según el caso pero siempre con prefijo:
  - `c-` componentes de diseño: `.c-card`, `.c-eyebrow`, `.c-precio`.
  - `u-` utilidades de un solo efecto: `.u-reveal`, `.u-oculto-movil`.
  - `woo-` ajustes de WooCommerce: `.woo-filtros`, `.woo-checkout`.
  - Nunca reutilizar ni sobrescribir directamente clases `.elementor-`, `.woocommerce-` o `.jet-` si se puede aplicar una clase propia.
- Nombres de plantillas: `Tipo – Nombre – Variante`. Ejemplos: `Sección – Hero – V1`, `Sección – Hero – V2 Editorial`, `Woo – Producto – V1`, `Global – Header`, `Global – Footer`. Las capas del navegador de Elementor también se nombran (ej. "Hero", "Tarjetas servicios").
- Rondas de cambios con el cliente:
  - Dirección visual: 1 ronda (elige una maqueta y pide ajustes sobre ella).
  - Web construida: 2 rondas.
  - Después, los cambios son trabajo extra o pasan al mantenimiento.
  - Una vez aprobada la maqueta, el estilo no se reabre: se pasa a construir. Si el cliente pide cambios de estilo después, señalarlo al usuario como fuera de alcance.

Si falta un dato del kit y es necesario para avanzar, pregúntalo una vez y sugiere al usuario añadirlo a esta skill.

## Ficha del proyecto en Notion

Cada cliente/proyecto tiene una página en la base de datos de Notion **"Proyectos web"** (está en la página SaaS Solutions, sección Gestión, encima de "Datos Clientes SaaS"). Es la memoria del proyecto: Claude la lee al empezar o retomar cualquier trabajo de ese cliente (desarrollo o mantenimiento) y la actualiza al cerrar cada etapa, sin que el usuario tenga que explicárselo.

- Si la base de datos no se encuentra, búscala en Notion por su nombre; solo si no existe, créala y pregunta una sola vez dónde ubicarla.
- Busca primero si ya existe una ficha del cliente antes de crear otra.
- Al empezar un proyecto nuevo, crea su página en la Etapa 1 con los datos del brief.

**Propiedades de la base de datos** (para filtrar y ver el estado de todos los proyectos):
Cliente, Tipo (Corporativa / Tienda), Encargo (Nueva / Rediseño / Cambios), País, Etapa actual (Entrada, Propuesta, Producción, Revisión, Cierre, Mantenimiento), Rondas visual usadas, Rondas web usadas, Fecha de inicio, Fecha de entrega, URL del sitio, URL de staging, Design System (enlace), Maquetas (enlace), Mantenimiento activo (sí/no), Último respaldo.

**Contenido de cada página (ficha técnica):**
- Infraestructura: hosting, dominio y dónde está registrado, servicio SMTP, URL de staging.
- Plugins del sitio y por qué se usan (ej. "JetEngine: campos de beneficios en productos").
- Estructura: plantillas del Theme Builder, secciones y variantes del kit usadas, campos y CPT de JetEngine, Query IDs de JetSmartFilters, widgets de ElementsKit en uso.
- CSS propio: clases personalizadas usadas y dónde.
- Legal: páginas publicadas, versión de país y fecha de la última revisión.
- Respaldos: dónde se guardan y fecha del último.
- Pendientes del cliente (datos que faltan).
- Historial de cambios después de la entrega (fecha y qué se hizo).

Lo visual (colores, fuentes, espaciado, movimiento, tono) **no se copia** en la ficha: vive en el Design System y la ficha solo lo enlaza, para que haya una sola fuente de verdad.

**Nunca guardes contraseñas ni claves en la ficha.** Solo anota dónde están (ej. "acceso en el gestor de contraseñas, entrada X"). Si el usuario o el cliente comparten una contraseña en la conversación, no la copies a Notion.

## Secuencia completa

**Preparación única (kit base, crece con cada proyecto):**
1. WordPress maestro con Hello Elementor, tema hijo y plugins del kit.
2. Capa de CSS del kit (clases `c-`, `u-`, `woo-`, regla `prefers-reduced-motion`, variables de movimiento `--dur-rapida`, `--dur-entrada` y `--curva`, respuesta al pulsar en botones, estado `:focus-visible` y hovers protegidos con `@media (hover: hover) and (pointer: fine)`).
3. Biblioteca de secciones con variantes (núcleo, corporativo, WooCommerce).
4. Plantillas del Theme Builder (header, footer, 404, blog, tienda) y plantillas legales base por país.
5. Exportado como archivo .wpress con All-in-One WP Migration para clonarlo en cada cliente (se vuelve a exportar cada vez que el kit crece).

**Por proyecto: 5 etapas, 2 aprobaciones**

| Etapa | Qué pasa | Intervención del usuario |
|-------|----------|--------------------------|
| 1. Entrada | El cliente entrega todo de una vez (brief, logo, referencias, contenido, datos legales). Claude crea la ficha en Notion, revisa y pide lo que falte en un solo mensaje. (Fase 1) | Reenviar el material |
| 2. Propuesta | Claude, sin paradas: analiza logo y referencias (o las busca), crea el Design System (incluye tono de voz) y 2 o 3 maquetas de portada con copy real. (Fases 2–4) | ✅ **Aprobación 1:** enviar el enlace al cliente; 1 ronda de cambios. Se congela el estilo. |
| 3. Producción | Claude: carga los globales sobre el kit clonado, decide el modelo de contenido, construye, completa copy, productos, SEO y páginas legales desde plantillas. (Fases 5–7) | Clonar el kit (.wpress) y dar acceso a WordPress (en un rediseño: acceso a la web actual y a un staging); validar datos legales con el cliente |
| 4. Revisión | Claude pasa primero la checklist en el navegador y corrige; luego revisa el cliente. (Fase 8) | ✅ **Aprobación 2:** 2 rondas. Se congela la web. |
| 5. Cierre | Respaldo, caché, correos, seguridad, panel limpio; ficha técnica completa en Notion; secciones nuevas al kit. (Fase 8) | Publicar y entregar |

En cada cambio de etapa, actualiza la propiedad "Etapa actual" y las rondas usadas en la ficha de Notion.

Las fases de abajo detallan cómo hacer cada parte; no son paradas. Claude las encadena dentro de cada etapa.

## Tipo de encargo: nueva, rediseño o cambios
Lo primero en la Etapa 1 es saber qué se pide, porque cambia el flujo. Si no está claro, se pregunta antes que nada y se anota en la propiedad "Encargo" de la ficha.

**A. Web nueva** (no hay web, o la actual se descarta sin conservar nada): flujo completo de 5 etapas.

**B. Rediseño** (hay web y se conserva contenido, URLs o posicionamiento):
- Antes de proponer: pedir URL y accesos; identificar tema, constructor, plugins, hosting y versiones de WordPress y PHP; hacer respaldo completo con copia fuera del servidor; auditar la web (Fase 2) y listar las URLs con tráfico (Search Console o Rank Math, si hay acceso).
- Elegir la vía y anotarla en la ficha:
  - **B1. Ya está en Elementor y la base está sana:** se rediseña sobre una copia en staging de la web actual. Se cargan los globales del nuevo Design System y se reconstruyen las secciones con la biblioteca del kit. No se importa el .wpress del kit.
  - **B2. Otro tema o constructor (Divi, WPBakery, Avada, Gutenberg…) o base muy desordenada:** se construye con el kit en un staging nuevo y se migra el contenido (páginas, entradas, medios; en tiendas productos, clientes y pedidos) con las herramientas de exportación e importación de WordPress y WooCommerce. Lo que se puede importar no se rehace a mano.
  - **No es WordPress:** como B2, migrando el contenido por CSV o a mano.
- Plugins existentes: inventariarlos antes de quitar nada. Los que cubre el kit se sustituyen; los que guardan datos (entradas de formularios, reservas, membresías) se conservan o se migran con cuidado.
- SEO: mantener las mismas URLs siempre que se pueda; las que cambien llevan redirección 301 en Rank Math. Si la web usaba otro plugin SEO, importar sus títulos y metadescripciones con el importador de Rank Math.
- Tienda en funcionamiento: mientras se trabaja en staging siguen entrando pedidos y clientes. Nunca reemplazar la base de datos de producción sin conservar los pedidos recientes; planificar el paso a producción en horario de poco tráfico y, si hay duda sobre cómo hacerlo, consultarlo con el usuario antes.
- Propuesta, aprobaciones y rondas: igual que en una web nueva.

**C. Cambios puntuales** (una sección nueva, un ajuste de diseño, una página extra en una web ya hecha):
- Sin Design System nuevo ni maquetas: se usan los globales y el Design System existentes. Leer primero la ficha de Notion; si la web no la hizo el usuario y no hay ficha, crearla con lo que se encuentre.
- Respaldo antes del cambio, staging si el cambio es grande, y registro en el historial de la ficha.
- Si el cambio afecta al estilo general de la web, ya es un rediseño (B): avisar al usuario antes de seguir.

## Fases del proyecto

### Fase 1. Brief
Pregunta solo lo que falte:
- Encargo: web nueva, rediseño o cambios puntuales (ver "Tipo de encargo"). Si ya hay web: URL, accesos y con qué está hecha.
- Tipo: corporativo o WooCommerce. Si es tienda: número aproximado de productos y categorías, pasarela de pago.
- ¿Tiene identidad de marca (logo, colores, fuentes) o se parte de cero?
- Negocio, público objetivo, competencia, objetivo principal de la web.
- Contenido disponible: textos, fotos reales, fotos de producto.
- País del negocio (Panamá, Venezuela u otro) y ciudades o zonas donde opera.
- Datos legales: razón social, identificación fiscal (RUC en Panamá, RIF en Venezuela), dirección, correo y teléfono de contacto.
- Para qué recoge datos personales (contacto, pedidos, newsletter, analítica, publicidad).
- Tono de voz deseado y 3 a 5 diferenciadores concretos con datos reales (años, clientes, cifras).
- Si es tienda: moneda(s), medios de pago, impuestos, zonas y costos de envío, política de cambios y devoluciones, garantía.

### Fase 2. Logo y referencias

**Si hay logo (o es lo único que hay)**, analízalo primero:
- Color: extrae los códigos exactos. Úsalos como acento y completa la paleta con neutros y derivados; comprueba contraste antes de usarlos en texto o botones.
- Forma: redondeado o anguloso, grueso o fino, geométrico u orgánico → radios, grosor de líneas, estilo de iconos.
- Tipografía: identifica el estilo; la web no repite la fuente del logo, la acompaña (logo expresivo → texto sobrio, y al revés).
- Personalidad: punto de partida de la dirección visual.
- Revisión técnica: ¿vector (SVG/AI/PDF) o solo imagen de baja calidad? ¿Versión horizontal, vertical, en blanco para fondos oscuros e ícono para favicon? Si faltan, pedir el original o preparar las versiones básicas.
- El logo no basta: completa con el brief, referencias y 2 o 3 webs de la competencia.

**Si es un rediseño (el cliente ya tiene web)**, audita primero la actual en el navegador (escritorio y móvil) antes de proponer nada: qué funciona y se conserva (contenido, estructura, posicionamiento SEO, URLs con tráfico), qué falla (señales de IA, jerarquía, legibilidad, rendimiento) y qué necesita el negocio que no está. Las URLs que cambien llevan redirección 301 en Rank Math.

**Referencias:**
- Pide 5 a 10 referencias (webs reales, Pinterest, capturas, incluso material impreso o físico) y también webs que el cliente NO quiere.
- Fuentes sugeridas: Awwwards, Land-book, Lapa Ninja, SiteInspire, Godly, Pinterest.
- Abre los enlaces en el navegador para ver el diseño real, no solo el texto. Revisa también la versión móvil.
- Advierte que muchos pines de Pinterest son conceptos irreales; equilibra con webs reales.
- Haz una **ficha de análisis** interna por referencia: paleta y proporción de color, tipografía y escala, recursos de composición, densidad y ritmo, tratamiento de imagen, y qué se toma de ella y por qué.
- Combina 3 a 5 referencias; nunca copies una sola. No se toman logos, ilustraciones propias ni diseños completos reconocibles; solo principios.
- Si el cliente no envía referencias, búscalas tú en su sector y entre marcas de personalidad parecida a la del logo, y úsalas directamente; las maquetas ya le dan al cliente opciones para elegir.
- El análisis alimenta el Design System. Solo crea un moodboard en un artifact de tipo Design si el usuario lo pide.

### Fase 3. Dirección visual y tokens
- Define una personalidad de 3 o 4 palabras con tensión entre ellas ("cálido pero preciso") y justifica cada decisión desde ella.
- Fija un **nivel de atrevimiento** del 1 al 5 según el sector y el brief (1–2 sobrio: despachos, salud, finanzas; 3 equilibrado; 4–5 expresivo: moda, gastronomía, creativos). Decide cuánta asimetría, cuántos recursos de composición, cuánto contraste tipográfico y cuánta intensidad de movimiento. Se anota en el Design System. Las 2 o 3 maquetas pueden explorar niveles contiguos (ej. 2 y 3) para que el cliente elija también el grado de riesgo.
- Tokens, con el formato de Ajustes del sitio de Elementor:
  - **Colores (roles fijos, valores por cliente):** Fondo, Superficie, Texto, Texto suave, Acento, Acento oscuro, Borde. Neutros cálidos o casi negros en lugar de blanco/negro puros.
  - **Tipografía:** máximo 2 fuentes (título con carácter + texto limpio), escala con proporción definida (ej. 1,25), tamaños H1–H6, párrafo, texto pequeño; valores para escritorio, tablet y móvil.
    - Párrafos con ancho máximo de 60–75 caracteres (ancho máximo del widget o contenedor, ej. `65ch` con unidad personalizada).
    - Interlineado que baja al crecer el tamaño: ~1,5–1,7 en texto, ~1,05–1,2 en títulos grandes. Espaciado entre letras ligeramente negativo en títulos grandes y positivo solo en mayúsculas pequeñas.
    - Máximo 3 pesos por familia. Títulos fluidos con `clamp()` (unidad personalizada de Elementor) cuando la escala salta mucho entre dispositivos.
  - **Forma:** radio de borde, grosor de líneas, sombras o ausencia de ellas.
  - **Espaciado:** escala fija (ej. 8, 16, 24, 32, 48, 64, 96) y densidad (aireada o compacta).
  - **Botones, formularios y enlaces:** estados normal y hover.
  - **Movimiento:** 2 o 3 duraciones (ej. 200 ms hovers, 600 ms entradas), una curva de aceleración, distancia de desplazamiento corta (ej. 16–24 px) y retardo de escalonado (ej. 100 ms). Ver "Sistema de movimiento".
- Elige 2 o 3 **recursos de composición** para el cliente (títulos enormes, eyebrows en mayúsculas, líneas finas, imágenes que rompen la cuadrícula, bloques de color a sangre, numeraciones grandes…). No todos.
- Reglas de imagen: tono, encuadre, proporciones; un único estilo de iconos o ninguno. En tiendas: proporción y fondo fijos para fotos de producto.
- Tono de voz: 3 rasgos (ej. "cercano, experto, directo"), propuesta de valor y diferenciadores.
- Plasma todo en un **artifact de tipo Design System** por cliente: paleta con roles, fuentes y escala, espaciado, radios y sombras, movimiento, tono de voz, componentes de muestra (botones, tarjetas, formularios), reglas de uso, y el logo con sus versiones. Es la fuente de verdad del cliente: de ahí salen los valores de los ajustes globales de Elementor y es la referencia para el mantenimiento futuro.

### Fase 4. Maquetas
- Crea 2 o 3 propuestas de portada con direcciones distintas en un **artifact de tipo Design** (lienzo con mesas de trabajo lado a lado), construidas con los tokens del Design System del cliente.
- El usuario puede editar el lienzo directamente y compartirlo con el cliente por enlace; los comentarios del cliente son la ronda de cambios de la maqueta. Si prefiere, se exporta a PDF o imagen.
- Tras la aprobación, se pueden maquetar en el mismo lienzo las páginas clave (ficha de producto, servicios, contacto).
- Claude Design no exporta a Elementor: lo aprobado se traduce en la Fase 5. Por eso las maquetas deben poder construirse con lo nativo de Elementor.
- Cada maqueta incluye versión móvil y textos con extensión realista, no relleno.
- Marca como "extra" cualquier elemento que Elementor no haga de forma nativa, para decidir si vale la pena.
- Indica qué elementos se animan y cómo (entrada, hover, scroll), para que el movimiento también se apruebe antes de construir.
- La maqueta es guía de estilo, no plano píxel perfecto, salvo que el usuario diga lo contrario.
- Lleva la cuenta de la ronda de cambios en curso y avisa cuando se agote.

### Fase 5. Traducción a Elementor
Para la propuesta elegida, define por sección una **ficha de construcción** (interna si construye Claude; se entrega solo si el usuario construye esa parte):
- Sección y variante de la biblioteca que se usa (o "nueva", y se añade al kit).
- Estructura de contenedores (dirección, columnas y proporciones, gap desde la escala).
- Widgets (Elementor Pro por defecto; ElementsKit si hace falta) y el global que usa cada elemento.
- Comportamiento en tablet y móvil (qué se apila, oculta o cambia de tamaño).
- CSS mínimo, solo si es imprescindible, con clases del kit y comentado.

Antes de las fichas, decide el **modelo de contenido**:
- ¿Hay contenido que se repite con la misma estructura y se actualizará con el tiempo (equipo, casos, servicios, sedes, bloques extra por producto)? Entonces JetEngine: define los CPT o meta boxes, los campos (nombre, tipo, obligatorio) y las plantillas de listado (Listing Grid) que los muestran.
- Si no, contenido directo en la página con widgets nativos, sin JetEngine.
- Los campos se nombran de forma clara y consistente entre proyectos (ej. `producto_beneficios`, `caso_cliente`) y se conectan con etiquetas dinámicas, para editar contenido sin tocar el diseño.

### Fase 6. Construcción
**Nunca se importa un .wpress sobre una web existente: reemplaza el sitio entero.** En un rediseño B1 no se importa el kit; se trabaja sobre una copia en staging de la web actual.

Primero la instalación (web nueva o rediseño B2): el usuario importa el kit base (.wpress con All-in-One WP Migration) en la instalación del cliente, idealmente en staging o subdominio, y se cargan los tokens del Design System en Ajustes del sitio (colores, fuentes, botones, formularios). Haz un respaldo antes de cambios grandes (importaciones de plantillas JSON, productos en lote).

Luego combina métodos según convenga:
- **Navegador** (wp-admin con sesión del usuario): cargar ajustes globales, construir o ajustar secciones, revisar. El usuario inicia sesión.
- **Plantillas JSON de Elementor** para importar: probar primero con una sección pequeña; con widgets Pro pueden requerir retoques.
- Cada sección terminada se guarda como plantilla y se incorpora a la biblioteca.

### Fase 7. Copy, SEO y páginas legales

**Copy**
- Parte del tono de voz y los diferenciadores del Design System. El copy de la portada ya se escribe en la Fase 4 y se reutiliza.
- Cada página es un recorrido: problema → solución → por qué creerte → qué hacer ahora. Cada sección del kit cumple una función en ese recorrido.
- Respeta la extensión que admite cada sección (títulos de 4 a 8 palabras, etc.).
- Textos específicos: datos, nombres, ejemplos concretos. Nada de relleno. Si falta un dato real, márcalo como pendiente para el cliente; nunca lo inventes.
- Usa expresiones y moneda del país del cliente, sin español neutro genérico.
- Corporativa: historia, servicios explicados por beneficio, casos, proceso, llamadas a la acción hacia contacto o WhatsApp.
- Tienda: descripciones por beneficio, detalles prácticos (tallas, materiales, uso), FAQ por producto, textos de confianza (envíos, cambios, medios de pago visibles).

**SEO (Rank Math)**
- Investiga palabras clave antes de escribir: una principal por página según lo que se busca en el sector y la ciudad.
- Título SEO, meta descripción, slug corto, un solo H1, encabezados jerarquizados, textos alternativos, enlaces internos.
- Corporativa: SEO local con ciudades y zonas reales, una página por servicio importante, schema de negocio local u organización, ficha de Google Business Profile, blog solo si el cliente lo mantendrá.
- Tienda: prioridad a las categorías, descripciones únicas (nunca copiadas del proveedor), schema de producto con precio y disponibilidad, URLs limpias.

**Páginas legales:** según el país y el tipo de web, ver "Páginas legales por país".

### Fase 8. Revisión
Antes de mostrar nada al cliente, recorre la web tú mismo con el navegador (escritorio y móvil) en dos pasadas y corrige lo que encuentres:
1. **Auditoría:** checklist final y "Señales de diseño hecho por IA".
2. **Pulido:** espaciados y alineaciones fuera de la escala, títulos con una palabra suelta en la última línea, estados hover/foco/pulsado en todo lo clicable, estados vacíos y de error en formularios y filtros, recortes de imagen coherentes. Solo pide capturas al usuario si no tienes acceso al sitio.

Notas de los plugins del kit al cerrar el proyecto:
- **LiteSpeed Cache:** activar al final, no mientras se diseña. Si la optimización de CSS/JS (minificar, combinar, carga diferida) rompe Elementor, animaciones o filtros, desactivar esa opción concreta. Verificar que carrito, checkout y mi cuenta quedan fuera de caché. Purgar caché tras cambios de diseño.
- **WP Mail SMTP:** enviar correo de prueba y probar formularios y un pedido de prueba.
- **Wordfence:** comprobar que no bloquea el editor de Elementor ni las peticiones AJAX de los filtros.
- **White Label CMS y Admin Notices Manager:** dejar el panel del cliente limpio y con la marca del usuario.
- **FileBird:** medios organizados por carpetas (páginas, productos, marca).
- **All-in-One WP Migration:** si se construyó en staging, migrar a producción con un .wpress. Hacer un respaldo completo al publicar y guardar una copia fuera del servidor.
- **ElementsKit:** desactivar los widgets y módulos que el sitio no usa.
- **Akismet:** activo solo si hay comentarios; si no hay blog, no se instala.

Al terminar: completar la ficha técnica en Notion, guardar en el kit base las secciones o variantes nuevas creadas en el proyecto y volver a exportar el .wpress del kit.

En mantenimiento posterior: leer primero la ficha del cliente y registrar en su historial cada cambio y cada respaldo.

## Señales de diseño hecho por IA

Lista de control para evitar el aspecto genérico. Una señal aislada no es un problema; varias juntas sí.

**Color y superficies**
- Degradados morado/azul/rosa, o degradados de fondo sin razón de marca.
- Paleta sin jerarquía: cinco colores con el mismo peso, sin un dominante, un apoyo y un acento.
- Modo oscuro con neones o brillos (glow) por defecto.
- Glassmorphism, blobs borrosos y manchas de color flotando detrás del contenido.
- Sombras grandes y difusas en todas las tarjetas.
- Fondo blanco puro con gris azulado frío cuando la marca pide otra temperatura.

**Tipografía**
- Inter, Poppins o Montserrat por defecto, una sola familia para todo.
- Títulos con degradado de color en el texto.
- Escala tímida: título apenas más grande que el párrafo, sin contraste de tamaño ni de peso.
- Mayúsculas con mucho espaciado en etiquetas pequeñas sobre cada título ("NUESTROS SERVICIOS") repetidas en todas las secciones.

**Composición**
- Todo centrado y simétrico.
- Hero con título centrado, subtítulo, dos botones (uno lleno y uno borde) y una captura o mockup flotando abajo.
- Filas de tres tarjetas idénticas con icono arriba, título y dos líneas, repetidas en cada sección.
- Rejilla de 3 o 4 columnas con iconos de línea genéricos (rayo, escudo, cohete, diana).
- Todas las secciones con el mismo padding y la misma altura, sin ritmo ni variación de densidad.
- Franja de estadísticas ("+500 clientes, 98% satisfacción") con cifras inventadas o redondas.
- Franja de logos de clientes inexistentes o testimonios con foto de stock.
- Sección final de "llamada a la acción" con fondo de color y botón centrado en cada página.

**Forma y detalles**
- Radios de borde grandes e iguales en todo (botones en píldora, tarjetas muy redondeadas).
- Emojis como iconos o viñetas.
- Iconos de un solo set genérico sin relación con el negocio.
- Insignias tipo "píldora" con punto de color y texto pequeño sobre el título del hero.
- Animaciones de entrada idénticas (fade-up) en absolutamente todo, o hover que escala las tarjetas.
- Tarjetas dentro de tarjetas, o todo el contenido metido en cajas con borde y sombra.
- Texto gris sobre fondos de color (se ve apagado y pierde contraste; usar un tono del propio fondo o el color de texto).
- Curvas con rebote o elásticas, y elementos que aparecen escalando desde cero.
- Botones y enlaces sin estado de foco visible o sin respuesta al pulsar.

**Imagen**
- Fotos de stock genéricas (equipo sonriendo en oficina, apretón de manos, laptop sobre escritorio).
- Ilustraciones 3D o abstractas sin relación con el sector.
- Imágenes sin tratamiento común: distinta luz, encuadre y color entre una y otra.

**Copy**
- Frases de relleno: "soluciones innovadoras", "llevamos tu negocio al siguiente nivel", "calidad y compromiso", "somos tu aliado estratégico".
- Estructuras repetidas: "No es X, es Y", tríos de adjetivos, titulares con dos puntos.
- Guiones largos en exceso y listas de tres elementos en cada párrafo.
- Español neutro sin referencias locales, sin cifras reales, sin nombres propios.
- Textos de botón vacíos: "Saber más", "Comenzar ahora" en todas partes.

**Cómo corregirlas (qué hacer en lugar de)**
- Elegir un dominante claro y un acento usado con disciplina; los neutros tienen temperatura acorde a la marca.
- Emparejar dos familias con contraste real (titular con carácter, texto muy legible) y una escala marcada.
- Romper la simetría al menos en el hero y en una sección más: alineación a la izquierda, rejillas asimétricas, una pieza que se sale de la cuadrícula.
- Variar el ritmo: secciones densas y secciones aireadas; no repetir dos veces seguidas el mismo patrón de tarjetas.
- Usar imágenes reales del cliente o fotografía con tratamiento unificado; si no hay, tipografía y formas de la marca antes que stock.
- Sustituir iconos genéricos por números, ilustración propia, fotos o ningún elemento.
- Copy con cifras, nombres, lugares y procesos reales del brief; si el dato no existe, se pide y no se inventa.
- Un detalle propio memorable por proyecto (una forma, un recurso tipográfico, una interacción) que salga del logo o del sector.

## Biblioteca de secciones
Cada sección tiene 2 o 3 variantes de layout. Varía layouts entre secciones consecutivas y prefiere la alineación a la izquierda.

**Núcleo (todos los proyectos):** header, footer, hero (texto a la izquierda / pantalla completa / editorial), llamada a la acción, testimonios, preguntas frecuentes, contacto, páginas legales, 404.

**Módulo corporativo:** servicios, equipo, casos o portafolio, proceso de trabajo, cifras, logos de clientes, blog (archivo y entrada).
Aquí la web es la marca: más expresión visual, tipografía protagonista, composición editorial.

**Módulo WooCommerce:** plantillas del Theme Builder (tienda, categoría, producto, carrito, checkout, mi cuenta) y secciones: destacado de producto individual, colección curada, producto en contexto, comparativa, bloques de confianza (envíos, garantía, pagos).

## Sistema de movimiento
El movimiento sigue la dirección visual del cliente, igual que color y tipografía. Una marca sobria se mueve lento y sin rebotes; una juvenil, más rápido y con más energía.

**Principios**
- Pocas animaciones y con propósito: señalar jerarquía, orden de lectura o interacción, no decorar. Animar el hero y 2 o 3 momentos clave, no todo.
- Nunca la misma animación de entrada en todos los elementos (el "aparecer desde abajo" repetido es un rasgo de estética genérica).
- Priorizar hovers cuidados (botones, tarjetas, imágenes) sobre entradas llamativas.
- Escalonar elementos en grupo (tarjetas, listas) con retardos cortos en lugar de animarlos en bloque.
- Coherencia: mismas duraciones y curva en toda la web.

**Reglas finas**
- Curva por defecto de salida suave (ease-out, ej. `cubic-bezier(0.22, 1, 0.36, 1)`). Nunca ease-in en entradas ni hovers: se sienten lentos al empezar.
- Interacciones (hover, pulsar, abrir menú) por debajo de 300 ms. Las salidas, más rápidas que las entradas.
- Animar solo `transform` y `opacity`, no tamaños, márgenes ni sombras grandes (rendimiento).
- Nada aparece desde `scale(0)`: partir de ~0,95 con opacidad.
- Botones con respuesta al pulsar (`:active` con `scale(0.97)`) y `:focus-visible` claro.
- Hovers solo en dispositivos con ratón (`@media (hover: hover) and (pointer: fine)`), para que no se queden pegados en móvil.
- Lo que el usuario repite muchas veces (menú, filtros, pestañas) se anima poco o nada.

**Herramientas de Elementor Pro**
- Animaciones de entrada, efectos de scroll y de ratón (Avanzado → Efectos de movimiento), transiciones de hover, transiciones entre páginas y efectos sticky.
- Las entradas nativas tienen curvas fijas y pocas duraciones. Para movimiento más refinado, usar clases reutilizables del kit (ej. `.u-reveal`) con la curva y duración del cliente, aplicadas desde el panel; siguen siendo editables al añadir o quitar la clase.

**Precauciones**
- Parallax y efectos de scroll: con moderación y desactivados o reducidos en móvil por rendimiento.
- Accesibilidad: el kit incluye una regla `prefers-reduced-motion` que anula o reduce animaciones.
- WooCommerce: sin animaciones en ficha de producto, carrito ni checkout; solo hovers.
- Transiciones entre páginas: solo en webs corporativas muy de marca, nunca en tiendas, porque hacen sentir la navegación más lenta.

## Reglas específicas de WooCommerce
- El producto es el protagonista. La marca se expresa con fuerza en portada, categorías y "nosotros"; en producto, carrito y checkout prima la claridad (precio, variantes, botón, envío, confianza).
- Catálogos pequeños: navegación directa sin megamenús; la portada puede mostrar productos; evitar cuadrículas grandes casi vacías y preferir destacados y colecciones curadas.
- Filtros con **JetSmartFilters**:
  - Solo los filtros que el catálogo justifica (con pocos productos, a menudo basta categoría y precio, o ninguno). Proponer cuáles según los atributos reales del cliente.
  - Conectarlos al widget de productos o de archivo de Elementor Pro mediante el Query ID, con filtrado AJAX y sin recarga.
  - Estilizarlos con los globales del sitio (colores, tipografía, radios, botones) para que no se vean como un componente externo; el CSS adicional va en el bloque de WooCommerce con clases del kit.
  - En móvil, filtros en un panel desplegable o botón "Filtrar", no encima de los productos.
  - Incluir estado vacío (sin resultados) y botón para limpiar filtros.
  - Guardar la combinación de archivo + filtros como plantilla del kit para reutilizarla.
- Ficha de producto como página de venta: beneficios, modo de uso, detalles, fotos en contexto, preguntas frecuentes, reseñas, venta cruzada. Si estos bloques varían por producto, crear sus campos con JetEngine (meta box en Productos) y mostrarlos con etiquetas dinámicas en la plantilla de producto, para que cada producto rellene sus bloques sin tocar el diseño. Ocultar los bloques cuyo campo esté vacío (visibilidad dinámica).
- Checkout: personalización mínima con widgets de Elementor Pro y globales; las pasarelas de pago que use el cliente pueden romperse con estilos agresivos.
- No sobrescribir plantillas PHP de WooCommerce en el tema.
- CSS de WooCommerce en un bloque separado y comentado.
- Rendimiento: pocos plugins, imágenes optimizadas, sin animaciones en páginas de producto.
- Claude puede redactar cada producto con cuidado (descripción, beneficios, FAQ, SEO) y preparar CSV de importación.

## Páginas legales por país

Reglas generales:
- Claude redacta a partir de plantillas base del kit y los datos del brief. Claude no es abogado: las plantillas base deben revisarse una vez con un abogado de cada país, y el cliente valida sus datos y condiciones antes de publicar. Dilo siempre al entregar.
- La normativa cambia: antes de redactar, busca en fuentes oficiales si hubo cambios recientes en el país del cliente.
- En todos los países: casilla de aceptación obligatoria en los formularios de Elementor enlazando a la política de privacidad; en WooCommerce, casilla de términos en el checkout y página de privacidad asignada en los ajustes.
- Banner y política de cookies si se usa analítica o píxeles publicitarios (plugin de cookies: [POR DEFINIR]).

**Panamá (país principal)**
- Todas las webs:
  - Política de privacidad según la Ley 81 de 2019 y su reglamento (Decreto Ejecutivo 285 de 2021); autoridad: ANTAI. Incluye responsable (razón social, RUC, dirección, correo), datos que se recogen y finalidad concreta, base del tratamiento (normalmente consentimiento), derechos ARCO y cómo ejercerlos.
  - Términos de uso.
- Tiendas (Ley 45 de 2007, Acodeco):
  - No existe derecho de retracto general (solo en ventas a domicilio), así que la **política de cambios y devoluciones la define el cliente** y debe ser muy clara: si acepta devoluciones por arrepentimiento, plazo, estado del producto, reembolso o nota de crédito, quién paga el envío.
  - Garantía: si el cliente no ofrece una propia, aplica la garantía mínima legal de 3 meses. Página o sección de garantías.
  - Ofertas: mostrar precio anterior y precio especial (artículo 64), también en banners diseñados a mano.
  - Términos de compra (precios con o sin ITBMS, medios de pago, envíos) y política de envíos.
  - Acodeco promueve una reforma de la Ley 45 para el comercio electrónico: verificar si ya se aprobó.

**Venezuela**
- No hay una ley especial de protección de datos; el marco es fragmentado (hábeas data constitucional y normas dispersas). Aplicar buenas prácticas: política de privacidad clara con responsable (razón social, RIF), finalidades, consentimiento, y cómo pedir acceso, rectificación o supresión.
- Tiendas: términos de compra, envíos, cambios, devoluciones y garantía claros; precios y moneda(s) explícitos; medios de pago que use el cliente. Verificar con abogado local la normativa de consumo y precios vigente.

**Otros países**
- Investiga la normativa vigente de datos personales y consumo en fuentes oficiales, resume las obligaciones para la web y márcalo para revisión de un abogado local antes de publicar.

## Checklist final
- [ ] Todos los colores y fuentes usan globales.
- [ ] Solo contenedores; nada de secciones/columnas antiguas.
- [ ] Widget HTML y CSS solo donde está justificado, con clases del kit y comentado.
- [ ] Capas y plantillas nombradas según la convención.
- [ ] Revisado en escritorio, tablet y móvil.
- [ ] Contraste y tamaños legibles; textos alternativos en imágenes.
- [ ] Revisada la lista "Señales de diseño hecho por IA": ninguna señal sin razón del brief.
- [ ] Textos reales y específicos; datos pendientes del cliente resueltos (nada inventado).
- [ ] Páginas legales según país y tipo de web, con datos del cliente validados; casillas de aceptación en formularios y checkout.
- [ ] Tienda: fotos consistentes, checkout probado con la pasarela real.
- [ ] Rendimiento revisado (peso de imágenes, plugins innecesarios) con LiteSpeed Cache activo y el sitio probado después de activarlo.
- [ ] Rank Math configurado en todas las páginas y productos.
- [ ] Correos probados con WP Mail SMTP (formularios y pedidos).
- [ ] Movimiento coherente con los tokens, sin animaciones repetidas en todo, reducido en móvil y respetando "reducir movimiento".
- [ ] Pasada de pulido hecha: espaciados en escala, estados hover/foco/pulsado en todo lo clicable, títulos sin palabras sueltas.
- [ ] Tienda: filtros probados en móvil, con estado vacío y opción de limpiar.
- [ ] Si se usó JetEngine: campos con nombres claros, bloques vacíos ocultos y edición de contenido probada sin tocar plantillas.
- [ ] Respaldo completo hecho al publicar, con copia fuera del servidor.
- [ ] Formularios protegidos contra spam (honeypot o reCAPTCHA; Akismet si hay comentarios).
- [ ] Ficha técnica en Notion completa y sin contraseñas; etapa marcada como Cierre o Mantenimiento.
- [ ] Secciones nuevas guardadas en la biblioteca del kit y .wpress del kit actualizado.