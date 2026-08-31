# 🍌 BLUEPRINT DIGITAL — PATACONCITOS
### Documento maestro del proyecto | Versión 2.1 — ✅ APROBADO | Elaborado por El Arquitecto

> **Estado: aprobado por el usuario como documento maestro oficial del proyecto** (con los 5 ajustes menores de esta versión incorporados). A partir de aquí el proyecto entra en **Fase 5 — Diseño**. Este documento sigue siendo vivo: se actualizará conforme se resuelvan las decisiones pendientes.
>
> **Regla que rige todo el documento (sin excepción):** ningún precio, producto, ingrediente, testimonio, tarifa, capacidad o métrica fue inventado. Todo lo no confirmado se marca con una de las 4 etiquetas de estado (ver abajo) — nunca se presenta como dato real.

### 🏷️ Sistema de etiquetas de estado (aplica a negocio, diseño, tecnología, menú, precios, marketing y automatizaciones)

| Etiqueta | Significado |
|---|---|
| ✅ **DECISIÓN CONFIRMADA** | Dato o decisión que el usuario declaró explícitamente. Se usa tal cual, sin modificar. |
| 🔶 **HIPÓTESIS** | Supuesto de trabajo razonable (ej. perfiles de cliente, ocasiones de consumo) que orienta el diseño pero aún no está probado con datos reales. |
| ⏳ **PENDIENTE DE VALIDACIÓN** | Dato que falta por definir o medir (precio, tarifa, capacidad, testimonio real). No se inventa bajo ninguna circunstancia. |
| 🧪 **PROPUESTA** | Ejemplo o sugerencia de El Arquitecto (nombre, copy, color) ofrecida para discusión, no para usar como definitiva sin aprobación. |

### 📐 Principios arquitectónicos transversales (aplican a todas las secciones y a todo desarrollo futuro)

1. **Regla de oro:** no se desarrolla ninguna funcionalidad cuya regla de negocio no haya sido validada — específicamente: tarifas de domicilio, pedido mínimo, capacidad máxima, tiempos de entrega, precios, productos y promociones. La arquitectura sí queda preparada para soportarlas (campos, estructuras y flujos ya definidos en las secciones 3, 5 y 14), pero no se automatiza ni se publica nada con esos valores hasta tener el dato real.
2. **No sobreconstruir:** se construye solo lo necesario para validar y hacer crecer a Pataconcitos en su etapa actual, dejando preparada la evolución futura sin implementar complejidad innecesaria (ver MVP vs. Futuro en cada sección).
3. **Infraestructura en paralelo:** el roadmap oficial (sección 16) mantiene sus 10 prioridades en orden, pero la investigación de **dominio + infraestructura básica** (disponibilidad, costos, alternativas — sección 15) puede adelantarse en paralelo desde ya, sin esperar a cerrar las decisiones comerciales. Esto es solo investigación/comparación — **no implica contratar ni configurar nada todavía**.
4. **Próximo gran entregable de negocio (antes del desarrollo técnico):** **Menú + Productos + Precios + Presentaciones + Fotografías.** Este paquete alimenta directamente la web, WhatsApp, el contenido de Instagram, la publicidad, la base de datos, la analítica y las automatizaciones futuras — es la pieza que más bloquea el resto del proyecto.

**Nota de reorganización de secciones (heredada de la v2.0, sigue vigente):**
- Se fusionaron "Rutas" + "Arquitectura de navegación" → sección 4.
- Se fusionaron "SEO" + "Analytics" + "Costos" → sección 15.
- Se fusionó "Roadmap" + "Especificación final para desarrollo" → sección 16.
- Esas 3 fusiones liberaron espacio para las secciones nuevas de la v2.0: **Menú y precios** (5), **Testimonios** (7) y **FAQ** (8). Ningún contenido se eliminó; todo quedó reubicado.

---

## 1. RESUMEN DEL PROYECTO

### Negocio
Pataconcitos vende productos a base de plátano verde y maduro (patacones, canastas, plátano aplastado, combinaciones), 100% por domicilio y pedido por encargo, atendido manualmente por Sara Restrepo vía WhatsApp (8:00 a.m.–5:00 p.m.). Cobertura: Medellín (zona principal) y Envigado, dentro del Área Metropolitana del Valle de Aburrá.

### Problema
No es (necesariamente) un problema de alcance — es un problema de **estructura**: no hay menú formalizado, no hay forma de saber si un cliente ya compró antes, no hay métricas, y las reglas de domicilio/pedido mínimo se deciden caso a caso.

### Cliente (hipótesis a validar, no dato cerrado)
Perfiles potenciales por **ocasión de consumo**: antojo individual, pareja, grupo de amigos/parranda, familia, reuniones/celebraciones, oficinas. El proyecto distingue Cliente (quién compra) / Consumidor (quién come) / Ocasión (cuándo y por qué), y el menú y el marketing deben organizarse también por ocasión, no solo por producto.

### Oferta
Preparaciones de plátano verde y maduro, canastas y plátano aplastado — el menú formal (nombres, categorías, combos, precios) **está en construcción**, no existe todavía como catálogo cerrado (ver sección 5).

### Competencia (resumen — detalle completo en `claude/analisis-competencia.md`)
10 negocios analizados en Medellín/Envigado. Hallazgos clave: (1) ningún competidor directo de patacón tiene web propia con menú/precios/cobertura claros — oportunidad estructural; (2) nadie es dueño de la ocasión "compartir" alrededor del patacón; (3) la experiencia de servicio en la categoría parece débil; (4) rango de precios de referencia en la categoría "para compartir" en Medellín: ~$12.000–$23.000 (solo referencia de mercado, no precio de patacón).

### Propuesta de valor (UVP)
⏳ **PENDIENTE DE VALIDAR.** No se asume un diferenciador. Se construirá cruzando producto real + competencia + cliente validado + ocasión de consumo + percepción de marca. Dirección apuntada: territorio de "antojo + compartir un momento", hoy vacío en la competencia analizada.

### Objetivo del proyecto digital
Convertir el recorrido **Instagram → Página web → Menú → Producto → WhatsApp → Pedido → Pago → Preparación → Domicilio → Seguimiento → Recompra** en un sistema medible, con WhatsApp como canal de conversión principal y Sara como administradora de la información operativa día a día.

---

## 2. STACK TECNOLÓGICO

*(sin cambios de fondo respecto a v1.0; se mantiene la recomendación)*

### Comparación de alternativas de arquitectura

| Opción | Descripción | Costo aprox./mes | Facilidad para Sara | Capacidad de crecer a IA/n8n | Complejidad de mantenimiento |
|---|---|---|---|---|---|
| A. Builder no-code (Wix, Squarespace) | Todo en plataforma cerrada | $15–30 USD | Alta | Baja — APIs limitadas | Baja, pero rígida |
| B. WordPress + plugin de catálogo | CMS abierto | $5–15 USD | Alta | Media — vía plugins/webhooks | Media |
| **C. Código a la medida + panel/CMS ligero** ⭐ | Frontend rápido (Next.js/Astro) + panel simple o Sheets/Airtable como fuente de datos | $0–10 USD + dominio | Media-Alta (diseñado a medida, tan simple como se necesite) | Alta — pensado desde el día 1 para WhatsApp API + n8n + IA | Media (mantenible junto con Claude) |

**Recomendación:** Opción C.

### Stack MVP
| Capa | MVP | Justificación |
|---|---|---|
| Frontend | Next.js o Astro, mobile-first | Rápido, SEO-friendly |
| Estilos | Tailwind CSS | Velocidad y consistencia |
| Contenido editable (menú, precios, testimonios, FAQ, fotos) | Panel simple a medida **o** Google Sheets/Airtable | Sara edita sin tocar código |
| Hosting | Vercel o Netlify | SSL incluido, despliegue simple |
| WhatsApp | Enlace `wa.me` con mensaje prellenado | Cero costo, cero integración compleja |
| Analytics | Google Analytics 4 + Meta Pixel | Gratuito, estándar |

### Futuro
Base de datos relacional (Supabase/Postgres), WhatsApp Business API + agente IA + n8n — ver sección 14.

---

## 3. BASE DE DATOS

Estructura ajustada a los campos que el usuario pidió mantener como mínimo necesario (sin campos innecesarios).

### Clientes
| Campo | Nota |
|---|---|
| id | identificador único |
| nombre | |
| whatsapp | identificador operativo principal |
| zona | |
| fecha_registro | |
| canal_adquisicion | Instagram, referido, otro |
| ultima_compra | fecha |
| frecuencia | calculada: pedidos / periodo |
| segmento | nuevo / ocasional / recurrente / frecuente / inactivo / recuperación |
| consentimiento_datos | booleano — requisito de privacidad (ver Decisiones pendientes) |

### Pedidos
| Campo | Nota |
|---|---|
| id | |
| cliente | relación a Clientes |
| fecha | |
| productos | referencia a Productos |
| cantidad | |
| subtotal | |
| domicilio | ⏳ pendiente de regla de tarifa |
| total | |
| metodo_pago | transferencia / efectivo |
| estado_pago | pendiente / por confirmar / confirmado / pagado / contra entrega |
| estado_pedido | pendiente / confirmado / en preparación / listo / despachado / entregado |
| direccion | |
| ocasion_consumo | antojo / pareja / familia / amigos-parranda / oficina / celebración (🧪 taxonomía propuesta) |

### Productos
| Campo | Nota |
|---|---|
| id | |
| nombre | ⏳ pendiente del menú definitivo |
| categoria | |
| descripcion | |
| ingredientes | ⏳ pendiente |
| precio | ⏳ pendiente |
| imagen | foto real |
| disponibilidad | booleano |
| producto_destacado | booleano |

### MVP vs. futuro
- **MVP:** las tres tablas de arriba en Google Sheets/Airtable — ya resuelve el problema de fidelización y de catálogo editable.
- **Futuro:** base de datos relacional (Supabase/Postgres), segmentación automática, historial completo conectado a WhatsApp Business API + n8n.

---

## 4. RUTAS Y ARQUITECTURA DE NAVEGACIÓN
*(sección fusionada — antes eran dos secciones separadas)*

### Rutas (MVP)
```text
/                      → Home
/menu                  → Menú y precios
/nuestros-productos    → Categorías y destacados (o integrado dentro de /menu, ver sección 6)
/testimonios           → Experiencias de clientes
/faq                   → Preguntas frecuentes
/cobertura             → Verificación de zona de domicilio
/nosotros              → Historia y marca
/contacto              → WhatsApp + formulario simple
/politica-privacidad   → Requisito legal (maneja datos de clientes)
```

### Rutas futuras
```text
/pedido        → Flujo de pedido guiado dentro de la web (si se decide no depender 100% de WhatsApp)
/promociones   → Cuando haya campañas recurrentes
/blog          → Contenido educativo, si se invierte en SEO de contenido
```

### Navegación
- **Menú principal (mobile, hamburguesa):** Inicio · Menú · Testimonios · FAQ · Cobertura · Nosotros · Contacto.
- **CTA principal (fijo/sticky):** "Pedir por WhatsApp" — visible en todo momento.
- **CTA secundario:** "Ver menú".
- **Footer:** redes, WhatsApp, horario (8am–5pm), zonas de cobertura, políticas.

---

## 5. MENÚ Y PRECIOS *(sección nueva)*

Esta sección define **cómo se estructura** el menú, no su contenido definitivo — el usuario fue explícito: **no inventar productos, ingredientes ni precios**.

### Estructura de datos del menú (reutiliza la tabla Productos de la sección 3)
Categoría → Producto → Nombre → Descripción → Ingredientes → Tamaño → Precio → Fotografía → Disponibilidad → ¿Destacado? → Combos asociados → Promociones asociadas.

### Estado actual (confirmado)
- Categorías generales conocidas: patacón verde, patacón maduro, canasta, plátano aplastado, combinaciones.
- Nombres comerciales: **exploratorios únicamente**, no definitivos (ej. "Canasta Pataconera", "El Aplastado" — 🧪 ejemplos, no catálogo real).
- Precios: **⏳ pendiente de definir** (depende de análisis de costos de producción y márgenes, aún no realizado).
- Ingredientes/toppings exactos por producto: **⏳ pendiente**.
- Producto(s) estrella: **⏳ pendiente**, se identificará una vez el menú esté formalizado y haya datos de ventas.

### Cómo se mostrará en la web (ejemplo de formato de tarjeta de producto — estructura, no contenido real)
```text
[Foto real del producto]
Nombre del producto (🧪 pendiente)
Descripción corta (🧪 pendiente)
Tamaño/presentación (🧪 pendiente)
Precio: "Información pendiente de definir" ← mientras no exista precio real
Botón: "Pedir por WhatsApp" (con mensaje prellenado mencionando el producto)
```

### Requisito de arquitectura
El menú debe administrarse desde el panel/Sheets definido en la sección 2 — actualizar un precio o marcar "agotado" un producto no debe requerir tocar código. Esto es no negociable dado que Sara necesita autonomía operativa total sobre esta información.

### MVP vs. futuro
- **MVP:** menú publicado en cuanto existan nombres, categorías y precios reales (aunque sea una primera versión simple, sin fotos profesionales todavía si no están listas — se usan las fotos reales que ya existen).
- **Futuro:** combos dinámicos, promociones con vigencia programada, recomendaciones de producto por ocasión de consumo.

---

## 6. SECCIONES DE LA PÁGINA PRINCIPAL (HOME)

Estructura revisada y adoptada según la propuesta del usuario, con ligeros ajustes de justificación:

1. **Hero** — Logo/mascota + foto real de producto + propuesta de valor + CTA principal "Pedir por WhatsApp" + CTA secundario "Ver menú".
2. **¿Qué es Pataconcitos?** — Presentación breve + concepto de marca (antojo, cercanía, compartir).
3. **Nuestros productos** — Categorías principales (patacón verde, maduro, canasta, aplastado) con productos destacados cuando existan.
4. **Menú y precios** — Enlaza o embebe la sección 5; muestra precios reales cuando estén definidos, o "información pendiente de definir" mientras tanto.
5. **Elige tu ocasión** — Antojo · Pareja · Amigos · Familia · Reunión · Parranda · Eventos (🧪 organiza el catálogo por ocasión, conecta con el hallazgo de mercado de la sección 1).
6. **Producto estrella** — Se activa cuando el/los producto(s) estrella estén identificados; mientras tanto, se omite o se reemplaza por "Producto destacado de la semana" con lo que ya exista.
7. **¿Por qué Pataconcitos?** — Diferenciadores **validados únicamente**; mientras la UVP no esté confirmada, esta sección se mantiene simple y honesta (frescura, preparación bajo pedido, atención cercana) sin afirmar superioridad no comprobada.
8. **Testimonios** — Experiencias reales (ver sección 7 nueva).
9. **Galería** — Fotos y videos reales de producto (nunca stock).
10. **Preguntas frecuentes** — Ver sección 8 nueva.
11. **Zona de cobertura** — Medellín, Envigado, Área Metropolitana según cobertura real confirmada.
12. **CTA final** — "¿Se te antojó?" + botón "Pedir por WhatsApp".
13. **Footer** — Instagram, WhatsApp, horarios, información básica, políticas.

*(Nota: se simplificó levemente el orden del usuario fusionando "Nuestros productos" y "Menú/Precios" como secciones consecutivas en vez de separarlas por una sección intermedia, para no duplicar el mismo catálogo dos veces seguidas en el recorrido — esto es una sugerencia de UX, no una eliminación de contenido.)*

---

## 7. TESTIMONIOS / EXPERIENCIAS DE CLIENTES *(sección nueva)*

### Estructura de datos (por testimonio)
| Campo | Nota |
|---|---|
| nombre_o_identificación | solo si hay autorización del cliente |
| fotografía | solo si hay autorización |
| producto_comprado | |
| comentario | texto real del cliente |
| calificación | opcional, ⏳ pendiente decidir si se usa (ej. estrellas 1–5) |
| fuente | WhatsApp, Instagram, otro |
| fecha | |
| autorización_uso | booleano — requisito antes de publicar cualquier testimonio |

### Estado actual
**⏳ No existen testimonios recopilados todavía.** Mientras tanto, la sección se publica con contenido de ejemplo, marcado explícitamente:

> 🧪 "Contenido pendiente de recopilar." — Aquí aparecerán las experiencias reales de quienes ya probaron Pataconcitos.

**No se inventan testimonios bajo ninguna circunstancia**, ni siquiera como placeholder con apariencia de real.

### Cómo se recopilarán (a definir e implementar más adelante, no en el MVP)
- Solicitar opinión por WhatsApp después de la entrega (conecta con el flujo de seguimiento de fidelización, sección 3/13).
- Capturar comentarios/menciones espontáneas en Instagram (con autorización antes de republicar).
- Formulario corto opcional post-compra.

### MVP vs. futuro
- **MVP:** sección visible con el mensaje de "pendiente de recopilar" — no bloquea el lanzamiento.
- **Futuro:** testimonios reales con foto/nombre autorizados, posible calificación, integrados también al feed de Instagram embebido.

---

## 8. PREGUNTAS FRECUENTES — FAQ *(sección nueva)*

Redactadas pensando en búsquedas naturales (ver también sección 15, SEO). Cada respuesta usa **solo información confirmada**; donde no hay dato, se declara explícitamente.

| Pregunta | Respuesta |
|---|---|
| ¿Qué es Pataconcitos? | Un negocio gastronómico de Medellín especializado en productos a base de plátano verde y maduro: patacones, canastas y plátano aplastado, preparados bajo pedido. |
| ¿Qué productos ofrecen? | Preparaciones de plátano verde y maduro, presentaciones tipo canasta y plátano aplastado. El menú detallado con nombres y precios está **pendiente de publicar**. |
| ¿Trabajan con plátano verde y maduro? | Sí, ambos son la base de la oferta. |
| ¿Cómo puedo realizar un pedido? | Escribiendo directamente por WhatsApp — el botón principal de la página te lleva allá. |
| ¿Los pedidos son bajo encargo? | Sí, actualmente todos los pedidos se preparan bajo encargo. |
| ¿Dónde realizan domicilios? | Medellín y Envigado, dentro del Área Metropolitana del Valle de Aburrá. |
| ¿Realizan domicilios en Medellín? | Sí. |
| ¿Realizan domicilios en Envigado? | Sí. |
| ¿Cuál es el horario de atención? | 8:00 a.m. a 5:00 p.m. |
| ¿Cómo puedo pagar? | Transferencia bancaria o efectivo. |
| ¿Aceptan efectivo? | Sí. |
| ¿Aceptan transferencia? | Sí. |
| ¿Cuál es el costo del domicilio? | **Información pendiente de definir** — actualmente se calcula según la zona y las condiciones del pedido. |
| ¿Existe pedido mínimo? | **Información pendiente de definir.** |
| ¿Cuánto tarda un pedido? | **Información pendiente de definir** — depende de la preparación y la zona de entrega. |
| ¿Puedo personalizar mi pedido? | Sí, la personalización de combinaciones es parte del modelo actual bajo pedido; el alcance exacto de personalización disponible se terminará de definir junto con el menú. |
| ¿Puedo hacer un pedido para una reunión o evento? | Sí, Pataconcitos atiende pedidos por encargo para grupos y reuniones; los detalles de capacidad para pedidos grandes están **pendientes de confirmar**. |
| ¿Cómo puedo comunicarme con Pataconcitos? | Por WhatsApp (canal principal) o Instagram [@pataconcitos.com_](https://www.instagram.com/pataconcitos.com_/). |

### MVP vs. futuro
- **MVP:** esta tabla, publicada tal cual, con los "pendiente de definir" honestos.
- **Futuro:** FAQ dinámica administrable desde el panel (Sara puede agregar/editar preguntas sin ayuda técnica), y eventualmente resuelta en primer nivel por el agente de WhatsApp con IA (sección 14).

---

## 9. TEXTOS Y TONO DE COMUNICACIÓN (COPYWRITING)

### Tono ajustado (confirmado por el usuario)
**Cercano + divertido + directo + antojador.** Humano, colombiano, alegre, fácil de entender, sin lenguaje corporativo ni exceso de formalidad, con personalidad, orientado al antojo y a compartir. Se evita cualquier frase genérica tipo "ofrecemos productos gastronómicos de alta calidad".

### Ejemplos de copy (🧪 referencias de tono, ninguno es slogan definitivo)
- Hero (ejemplo): "¿Se te antojó? 🍌 Nosotros ponemos el patacón, tú pones el parche." — *(referencia de tono dada por el usuario, no aprobada como slogan final)*
- CTA principal: **"Pedir por WhatsApp"**
- CTA secundario: **"Ver menú"**
- CTA final (sección 12 del Home): **"¿Se te antojó?"** + botón de WhatsApp.
- Mensaje de bienvenida en WhatsApp (ya definido en el proyecto): "¡Hola! 👋 Bienvenido a Pataconcitos 🍌🔥 Con mucho gusto te ayudamos. ¿Quieres ver nuestro menú o realizar directamente un pedido?"
- Mensaje fuera de horario (🧪 propuesta): "¡Gracias por escribir a Pataconcitos! 🍌 Atendemos de 8:00am a 5:00pm — te respondemos apenas estemos por aquí."

### Reglas de redacción para todo el sitio
- Nunca lenguaje corporativo/gourmet ("exquisito", "alta cocina", "experiencia culinaria excepcional").
- Frases cortas, directas, con guiños colombianos y a la ocasión de compartir.
- Cualquier dato numérico (precio, tiempo, costo) solo se escribe si es real — de lo contrario, "información pendiente de definir".

---

## 10. DIRECCIÓN VISUAL

*(sin cambios de fondo — se reafirma la decisión de no crear marca nueva)*

**Punto de partida (confirmado):** logo real — sello circular, banano-chef con gorro y guantes, texto perimetral "PATACONCITOS.COM" / "UNA DELICIA AL PALADAR", "cuentas" de colores simulando topping de patacón, dos estrellas naranjas.

**Paleta observada (base real):** azul petróleo/gris oscuro (fondo/anillo interior), dorado/amarillo mostaza (anillo exterior, tagline), naranja (anillo intermedio, estrellas), blanco (texto, guantes), amarillo-verde (plátano del personaje).

**Aplicación web propuesta:**
| Uso | Color |
|---|---|
| Primario (header/footer) | Azul petróleo |
| Acento CTA ("Pedir por WhatsApp") | Naranja o dorado |
| Fondo general | Blanco o crema cálido |
| Detalles/iconografía | Verde del plátano |

**Tipografía:** 🧪 propuesta — redondeada/amigable para títulos, sans-serif legible para cuerpo, priorizando lectura mobile.

**Fotografía:** producto real, luz cálida, primeros planos de textura/crocante, ambiente de "parche" — nunca banco de imágenes.

**Botones/cards:** esquinas redondeadas (coherentes con el sello circular del logo), sombras suaves.

**Contenido visual a producir (no existe aún):** fotos profesionales por producto una vez el menú esté formalizado, videos verticales de preparación, fotos de entrega/experiencia.

---

## 11. UX/UI

- Jerarquía visual: producto y CTA de WhatsApp siempre por encima de texto institucional.
- Mobile-first real: diseño y pruebas parten de viewport móvil.
- Botón de WhatsApp fijo/flotante en toda la navegación.
- Formularios mínimos (contacto), nunca un reemplazo del flujo por WhatsApp.
- Accesibilidad: contraste cuidado especialmente con el dorado sobre blanco, alt-text en fotos de producto.
- Microinteracciones ligeras al navegar por ocasiones/categorías, sin sacrificar velocidad.
- FAQ y testimonios con diseño escaneable (acordeón para FAQ, tarjetas para testimonios).

---

## 12. ESTRATEGIA DE CONVERSIÓN

### Funnel objetivo (confirmado, es el eje de todo el blueprint)
**Instagram → Página web → Menú → Producto → WhatsApp → Pedido → Pago → Preparación → Domicilio → Seguimiento → Recompra**

### CTA
- **Principal: "Pedir por WhatsApp"** — presente en Hero, navegación fija, menú, producto destacado y CTA final.
- **Secundario: "Ver menú"**.
- Terciarios: "Verificar cobertura", "Síguenos en Instagram", "Escríbenos tus dudas" (enlaza a FAQ o WhatsApp).

### Puntos de abandono probables (a validar con datos reales una vez el sitio esté activo)
- Cliente no sabe si Pataconcitos entrega en su zona → mitigado con sección de cobertura visible.
- Cliente no encuentra precios claros → brecha real mientras el menú no esté formalizado; se comunica con transparencia ("información pendiente de definir") en vez de ocultarlo.
- Cliente escribe fuera de horario → mitigado con mensaje automático básico de WhatsApp Business.

### Elementos de confianza
FAQ resuelta con honestidad, testimonios reales cuando existan, fotos/video reales, transparencia sobre lo que aún está pendiente (genera confianza en vez de restarla).

---

## 13. WHATSAPP

### Botón y mensajes
Enlace `wa.me` con mensaje prellenado según el origen (ej. desde una tarjeta de producto: "Hola, quiero pedir [nombre producto] de Pataconcitos"). Mensajes de bienvenida y fuera de horario ya definidos en la sección 9.

### Flujo de conversación
Consulta → Selección de producto → Confirmación → Datos de domicilio → Verificación de cobertura → Cálculo de total (productos + domicilio, cuando exista regla) → Método de pago → Confirmación final → Preparación → Despacho → Entrega → Seguimiento → Solicitud de testimonio/opinión (alimenta la sección 7).

### FAQ dentro de WhatsApp
Las mismas preguntas de la sección 8 deben poder resolverse ahí, manual por ahora (Sara), automatizable después (sección 14).

### Preparación para IA/n8n
Cada paso del flujo está diseñado para mapearse a un nodo de automatización cuando se decida escalar — sin implementarlo todavía.

---

## 14. AUTOMATIZACIÓN E INTELIGENCIA ARTIFICIAL (evolución progresiva)
*(sección fusionada — automatización e IA se presentan juntas porque el usuario las definió como una sola línea evolutiva de 4 etapas)*

```text
Etapa 1 — Actual        → Atención 100% manual por Sara vía WhatsApp.
Etapa 2 — Asistida       → WhatsApp + respuestas rápidas/plantillas + registro manual de clientes/pedidos en hoja de datos.
Etapa 3 — Automatizada   → WhatsApp Business API + n8n: registro automático de pedidos, mensaje de seguimiento post-entrega, verificación automática de cobertura por zona.
Etapa 4 — Inteligente    → Agente IA de primer nivel (FAQs, menú, toma de pedido) + segmentación de clientes + recomendaciones + fidelización + analítica avanzada — con derivación a Sara cuando se requiera atención personalizada (la IA nunca la reemplaza por completo).
```

**No se implementa ninguna etapa más allá de la 1 (actual) en este momento.** Esta sección solo deja la arquitectura (base de datos, flujo de WhatsApp, estructura de menú) lista para poder evolucionar sin rediseñar todo desde cero.

**Automatizaciones priorizadas para cuando se decida escalar (impacto/esfuerzo):**
1. Registro automático de pedidos a base de datos (alto impacto, esfuerzo medio).
2. Mensaje de seguimiento post-entrega (alto impacto en fidelización, esfuerzo bajo).
3. Verificación automática de cobertura por zona (impacto medio, esfuerzo bajo — requiere regla de zonas definida primero).
4. Agente IA completo para pedidos (impacto alto, esfuerzo alto — para cuando el volumen lo justifique).

---

## 15. SEO, ANALÍTICA Y COSTOS
*(sección fusionada — antes eran 3 secciones separadas)*

### SEO local
**Keywords naturales priorizadas** (sin forzar, redactadas dentro de frases reales): "patacones en Medellín", "patacones a domicilio Medellín", "patacones en Envigado", "comida a domicilio Medellín", "comida para compartir", "canastas de patacones", "comida para reuniones", "domicilios de comida".

- Meta title (🧪 propuesta): "Pataconcitos | Patacones y plátano a domicilio en Medellín y Envigado"
- Meta description (🧪 propuesta): "Pide tus patacones y canastas de plátano favoritas a domicilio en Medellín y Envigado. Frescos, para compartir, directo por WhatsApp."
- H1 sugerido: "Patacones y plátano a domicilio en Medellín y Envigado"
- **Google Business Profile** (gratuito, alto impacto): categoría "comida a domicilio", zona de servicio Medellín/Envigado, horario 8am–5pm.
- Consistencia de NAP entre Instagram, Google Business y la web.
- Schema.org `Restaurant`/`LocalBusiness` en el código.
- FAQ (sección 8) redactada pensando en búsquedas naturales — ya cumple esta función.

### Analítica — KPIs iniciales (simples, MVP)
| Grupo | KPI |
|---|---|
| Marketing | Visitas al sitio, fuente de tráfico (Instagram → Web), clics al botón de WhatsApp |
| Ventas | Conversaciones iniciadas, pedidos, tasa de conversión, ticket promedio, ventas totales |
| Fidelización | Clientes nuevos, clientes recurrentes, tasa de recompra |
| Producto | Productos más vendidos, productos menos vendidos |

Herramientas MVP: Google Analytics 4 (visitas, fuente, eventos de clic a WhatsApp) + registro manual en hoja de cálculo (conversaciones, pedidos, ventas — mismos campos de la sección 3).

**Futuro:** dashboard consolidado (Looker Studio conectado a Sheets o BD), KPIs de operación (tiempos de respuesta/preparación/entrega) y de marketing avanzado (CAC, ROAS) una vez haya inversión paga y volumen suficiente.

### Costos aproximados (Económica / Recomendada / Escalable)
| Componente | Económica | Recomendada | Escalable |
|---|---|---|---|
| Dominio (.com) | ~$12–15 USD/año | igual | igual |
| Hosting | Gratis (Vercel/Netlify free) | Gratis–$20 USD/mes | $20–50+ USD/mes |
| Correo corporativo | Gratis (alias) | ~$6 USD/mes/usuario (Google Workspace) | igual, se suman usuarios |
| Base de datos | Gratis (Sheets) | Gratis–$25 USD/mes (Supabase) | $25+ USD/mes |
| CMS/panel | Incluido en desarrollo a medida (Sheets como fuente) | Panel a medida simple (costo único de desarrollo) | CMS headless con más funciones |
| WhatsApp | Gratis (enlace wa.me) | Gratis (WhatsApp Business app) | WhatsApp Business API — costo variable por conversación |
| n8n | No aplica en MVP | Gratis (self-hosted) o ~$20 USD/mes (cloud) | Según volumen |
| IA (agente conversacional) | No aplica en MVP | Costo por uso de API, bajo volumen inicial | Costo por uso, crece con conversaciones |
| Analytics | Gratis (GA4 + Meta Pixel) | Gratis | Herramientas de pago si se requiere |

*Cifras orientativas de mercado para dimensionar la decisión — no son cotizaciones cerradas.* **No se contrata ni implementa nada todavía** — esto es insumo para decidir.

---

## 16. ROADMAP Y ESPECIFICACIÓN TÉCNICA FINAL
*(sección fusionada — antes eran "Roadmap" y "Especificación final para desarrollo")*

### Roadmap priorizado (orden confirmado por el usuario)
1. **Formalizar menú y productos** — bloqueador de todo lo demás.
2. Definir precios y estructura de costos.
3. Definir política de domicilio (tarifa por zona + pedido mínimo).
4. Recopilar fotografías y videos reales.
5. Validar la propuesta de valor frente a la competencia.
6. Definir dominio e infraestructura *(confirmado: esta investigación —disponibilidad de dominio, costos y alternativas de hosting— puede adelantarse EN PARALELO desde ya, sin esperar a cerrar las decisiones comerciales. No implica contratar ni configurar nada todavía; se mantiene en la posición 6 del roadmap oficial, pero su exploración no está bloqueada por las prioridades 1–5)*.
7. Construir el MVP de la web.
8. Integrar analítica (GA4 + Google Business Profile).
9. Integrar automatización (registro automático, mensaje de seguimiento).
10. Implementar IA y fidelización avanzada.

### Especificación técnica (para cuando se decida iniciar desarrollo — no ahora)
**Estructura de carpetas sugerida:**
```text
/pataconcitos-web
  /app (o /pages)
    /, /menu, /testimonios, /faq, /cobertura, /nosotros, /contacto, /politica-privacidad
  /components
    Header, Footer, WhatsAppButton, ProductCard, TestimonialCard, FAQAccordion, CoverageChecker, HeroSection, OcasionSelector
  /data
    menu.json, testimonios.json, faq.json, zonas-cobertura.json (o conexión a Sheets/Airtable)
  /public/images (fotos/videos reales)
  /styles (tokens de color de marca)
```
**Componentes clave:** `WhatsAppButton` (sticky, mensaje dinámico), `ProductCard`, `OcasionSelector`, `CoverageChecker`, `TestimonialCard`, `FAQAccordion`.

**Integraciones MVP:** `wa.me`, GA4, Google Business Profile.
**Integraciones futuras:** WhatsApp Business API, n8n, proveedor de IA conversacional, Supabase/Postgres.

**Reglas de negocio a codificar solo cuando estén definidas:** tarifa de domicilio por zona, pedido mínimo, capacidad de saturación.
**Reglas de diseño:** mobile-first, paleta/tipografía del logo real, solo fotos reales.
**Reglas de conversión:** cada sección del Home lleva a una acción; CTA "Pedir por WhatsApp" siempre visible.
**Reglas de SEO:** metadatos por página, schema `LocalBusiness`, alt-text descriptivo.

---

## 🚩 DECISIONES PENDIENTES (clasificadas por prioridad)

| Decisión | Prioridad |
|---|---|
| Menú definitivo (nombres, categorías, presentaciones) | **Alta** |
| Productos definitivos | **Alta** |
| Ingredientes/toppings por producto | **Alta** |
| Precios | **Alta** |
| Pedido mínimo | **Alta** |
| Costo del domicilio por zona | **Alta** |
| Dominio (nombre y disponibilidad) | **Alta** |
| Hosting definitivo | **Alta** |
| Política de privacidad | **Alta** |
| Política de tratamiento de datos de clientes | **Alta** |
| Zonas exactas de cobertura dentro del Valle de Aburrá | **Media** |
| Capacidad de producción real (pedidos/día) | **Media** |
| Tiempo de preparación real | **Media** |
| Tiempo de entrega real | **Media** |
| Método exacto de transferencia (banco/cuenta a mostrar al cliente) | **Media** |
| Testimonios reales recopilados | **Media** |
| Fotografías/videos profesionales | **Media** |
| Política de pedidos/cancelaciones | **Media** |
| Decisión panel a medida vs. Sheets/Airtable | **Media** |
| Paleta de colores exacta (HEX) y tipografías definitivas | **Baja** |
| Correo corporativo (contratar ahora o después) | **Baja** |
| Uso o no de calificación por estrellas en testimonios | **Baja** |

---

## ✅ PRÓXIMOS PASOS

**PRIORIDAD 1** — Formalizar menú y productos.
**PRIORIDAD 2** — Definir precios y estructura de costos.
**PRIORIDAD 3** — Definir política de domicilio (tarifa + mínimo).
**PRIORIDAD 4** — Recopilar fotografías y videos reales.
**PRIORIDAD 5** — Validar propuesta de valor frente a competencia.
**PRIORIDAD 6** — Definir dominio e infraestructura *(su investigación —no su contratación— puede adelantarse en paralelo desde ya, ver nota en sección 16)*.
**PRIORIDAD 7** — Construir el MVP de la web.
**PRIORIDAD 8** — Integrar analítica.
**PRIORIDAD 9** — Integrar automatización.
**PRIORIDAD 10** — Implementar IA y fidelización avanzada.

---

## 🔍 CRITERIOS DE APROBACIÓN DEL BLUEPRINT

| Criterio | Estado |
|---|---|
| No hay información inventada (precios, productos, testimonios, métricas) | ✅ Cumplido — todo lo no confirmado está marcado como pendiente o ejemplo |
| Las hipótesis están claramente identificadas (UVP, cliente, ocasión) | ✅ Cumplido |
| El MVP es realista (no sobreconstruido) | ✅ Cumplido — MVP usa herramientas gratuitas/económicas y procesos manuales donde aún no se justifica automatizar |
| La arquitectura es escalable hacia IA/n8n/BD relacional | ✅ Cumplido — ver secciones 2, 3 y 14 |
| La página está orientada a conversión, no solo institucional | ✅ Cumplido — funnel y CTA definidos en sección 12 |
| WhatsApp es el canal principal de pedidos | ✅ Cumplido |
| Sara puede administrar la información operativa sin ayuda técnica | ✅ Cumplido — panel/Sheets definidos en secciones 2 y 5 |
| La identidad visual respeta la marca actual (no se crea una nueva) | ✅ Cumplido — sección 10 parte del logo real |
| Testimonios, FAQ y precios están incluidos en la estructura | ✅ Cumplido — secciones 5, 7 y 8 |
| La solución es mobile-first | ✅ Cumplido — sección 11 |
| El costo de operación inicial es razonable | ✅ Cumplido — MVP con componentes gratuitos o de muy bajo costo (sección 15) |

**✅ Blueprint aprobado por el usuario como documento maestro oficial del proyecto Pataconcitos.** El proyecto avanza a **Fase 5 — Diseño**. No se ha iniciado programación ni configuración técnica todavía.

---

## 🎨 REGISTRO DE FASE 5 — DISEÑO (avance)

| Paso | Entregable | Estado |
|---|---|---|
| 1 | Dirección creativa (paleta extraída del logo, tipografía, tono) | ✅ Aprobado |
| 2 | Wireframes (estructura de Home, Menú, Testimonios, FAQ, componentes) | ✅ Aprobado |
| 3 | Dirección creativa de alta fidelidad (paleta HEX definitiva, escalas, muestra conceptual) | ✅ Aprobado |
| 4 | Design System (colores, tipografía, botones, cards, componentes, estados) | ✅ Aprobado |
| 5 | Home completa — alta fidelidad (mobile) | ✅ Aprobado |
| 6 | Menú — alta fidelidad (filtros, tarjetas, disponibilidad) | ✅ Aprobado |
| 7 | Detalle de producto — alta fidelidad | ✅ Aprobado |
| 8 | Testimonios — alta fidelidad (estado real + estructura futura marcada como ejemplo) | ✅ Aprobado |
| 9 | FAQ — alta fidelidad (acordeón agrupado por objeción) | ✅ Aprobado |
| 10 | Responsive desktop (Home) | ✅ Aprobado |
| 11 | Revisión UX/UI | ✅ Completada — ver hallazgos abajo |
| 12 | Correcciones | ✅ Aplicadas (ver detalle abajo) |
| 13 | Aprobación final del diseño completo | ✅ Aprobado |
| 14 | Construcción (MVP web real) | ✅ Completada — ver Fase 6 abajo |

### Hallazgos de la revisión UX/UI y correcciones aplicadas

1. **[Alta — corregido]** Contraste insuficiente: texto blanco sobre el naranja `#D9631F` en botones/chips pequeños (~3.46:1, no alcanza el mínimo de 4.5:1 en texto bajo 18.66px). **Corrección:** todos los botones primarios, chips activos y el CTA sticky pasan a usar el naranja profundo `#B64E14` como fondo (contraste ~4.83:1, cumple WCAG AA). El naranja original `#D9631F` se conserva para acentos grandes, badges y decoración donde no hay texto pequeño encima.
2. **[Media — corregido]** El overlay oscuro del Hero mobile podía perder legibilidad sobre fotos reales muy claras. **Corrección:** se reforzó el degradado oscuro (de 35%/92% a 55%/93% de opacidad) y se añadió `text-shadow` al titular como resguardo adicional, independientemente de qué tan clara sea la foto real que se use después.
3. **[Baja — corregido]** La caja de "precio pendiente" con borde punteado podía leerse como un campo roto/deshabilitado. **Corrección:** se añadió el ícono 🔔 junto al texto en todas las pantallas (Home, Menú, Detalle de producto) para reforzar que es un estado temporal cuidado, no un error.
4. **[Media — resuelto en construcción]** Los estados `:focus-visible` quedaron implementados globalmente en el MVP (outline naranja profundo de 3px en todo elemento enfocable).

---

## 🚀 REGISTRO DE FASE 6 — CONSTRUCCIÓN Y PUBLICACIÓN (MVP)

**Estado: MVP construido y publicado como página privada.** No es todavía la web pública final en dominio propio — es el sitio funcional real, listo para compartir cuando el usuario decida.

### Qué se construyó
Un sitio de una sola página con navegación real entre secciones (Inicio, Menú, Detalle de producto, Testimonios, FAQ) mediante rutas por hash (compartibles), reutilizando el Design System aprobado (colores, tipografía, componentes) y las 3 correcciones de accesibilidad del Paso 9/11.

**Funcionalidad real, no maqueta:**
- CTA "Pedir por WhatsApp" enlaza a `https://wa.me/573007374615` con mensaje prellenado — funcional en Header, Hero, sticky mobile y CTA final.
- ✅ **DECISIÓN CONFIRMADA** — Número de WhatsApp: **+57 300 737 4615**.
- Filtros de menú, acordeón de FAQ (agrupado por tema) y apertura de detalle de producto funcionan con JavaScript real, no son solo imágenes estáticas.
- Enlace real a Instagram `@pataconcitos.com_`.
- Navegación mobile (hamburguesa) y desktop (barra horizontal) — layout reflowed, no solo estirado.
- `prefers-reduced-motion` respetado y foco de teclado visible en todos los elementos interactivos.

**Lo que sigue honestamente marcado como pendiente (no se inventó nada):**
- Menú, nombres de producto, ingredientes y precios: 🧪 propuesta de ejemplo / 🔔 pendiente de definir.
- Testimonios: estado real "Próximamente", con una única estructura de ejemplo marcada "EJEMPLO — NO REAL".
- Tarifa de domicilio, pedido mínimo, horario de atención: 🔔 pendientes en el footer y en el FAQ.

### Publicación
- **✅ Publicado en producción vía GitHub Pages:** https://jotalexe.github.io/pataconcitos-web/ — pública, sin autenticación, accesible desde cualquier navegador.
- Repositorio fuente: `github.com/jotalexe/pataconcitos-web` (subido por Claude vía navegador, ya que el conector de GitHub no llegó a activarse en la sesión). Incluye `index.html` (el sitio) y `/docs` (blueprint, análisis de competencia, entrevista y las 10 piezas de diseño de alta fidelidad, todo como referencia histórica del proceso).
- Sigue sin ser dominio propio (`pataconcitos.com`) — se usa el dominio gratuito que da la plataforma (`github.io`), tal como se acordó (no se compra ni configura dominio propio todavía).
- Cuando exista un dominio propio, se apunta como "custom domain" en GitHub Pages sin rehacer el sitio.

### MVP vs. futuro
- **MVP (hecho):** sitio funcional de una página, WhatsApp real, contenido pendiente marcado con honestidad.
- **Futuro:** dominio propio, panel/Sheets para que Sara edite el menú sin ayuda técnica, base de datos real, analítica (GA4), automatización y agente IA — sin implementar nada de esto todavía.

### Actualización — Redes sociales, WhatsApp y fotos reales de producto
Sobre el MVP aprobado se hicieron únicamente los siguientes ajustes (sin tocar paleta, tipografía, logo, estructura ni copy aprobados):

- **Iconos sociales oficiales en el footer:** Instagram y WhatsApp como íconos reales y clicables (abren en pestaña nueva); Facebook se dejó preparado visualmente pero **sin enlace** (mostrado en estado "pendiente", no clicable) porque no se ha confirmado una URL real — no se inventó ningún perfil.
- **Botones "Pedir por WhatsApp" reducidos:** se eliminaron los duplicados del header y del menú móvil. Quedan exactamente: CTA principal del Hero, CTA final tras la sección de productos, CTA sticky en móvil, y el CTA contextual "Preguntar por este producto" en el detalle de cada producto.
- **Ícono oficial de WhatsApp:** se reemplazó el emoji 💬 por el ícono SVG oficial de WhatsApp (glifo del teléfono en burbuja) en los 5 botones que quedaron, siempre acompañado del texto.
- **Fotos reales de las 3 canastas:** se incorporaron las fotos reales de Canasticas, Paquete Grande y Paquete Mediano suministradas por el negocio, recortadas para eliminar gráficos de marketing superpuestos (logo, banners de precio) y mejoradas fotográficamente (color, contraste, nitidez) sin alterar el producto ni agregar ingredientes que no estuvieran en la foto original. El nombre del producto se mantiene como texto HTML (no quemado en la imagen) para SEO/accesibilidad.
- Verificado en vivo en `https://jotalexe.github.io/pataconcitos-web/`: Hero, Menú (3 tarjetas con foto real), detalle de producto y footer con los 3 íconos sociales.

**🔔 Pendiente de confirmar con Sara:** las imágenes que llegaron de "Paquete Grande" y "Paquete Mediano" muestran precios visibles en el material de marketing original ($5.500 y $4.500 respectivamente). El sitio **no los adoptó** — sigue mostrando "🔔 Precio pendiente" — porque no hubo una instrucción explícita de tomar esos precios como definitivos. Falta que el usuario confirme si esos son los precios reales y vigentes antes de publicarlos en el sitio.

---

*Fin del Blueprint v2.1 — Aprobado. Documento vivo — se actualizará conforme se resuelvan las decisiones pendientes.*
