# Entrevista El Arquitecto — Pataconcitos

Notas en construcción durante la entrevista estructurada para el blueprint digital.

## FASE 1 — DESCUBRIMIENTO ✅ (completa)
- 100% domicilios/encargo, sin local físico.
- Producto: patacones verde/maduro, canastas, aplastado, combinaciones.
- Flujo deseado: Instagram → Web → Menú → Verificar cobertura → WhatsApp → Pedido → Domicilio.
- Cobertura: Medellín (principal) + Envigado, Área Metropolitana.
- Menú aún no formalizado — entregable a construir (nombres exploratorios listados, no definitivos).
- Problema principal: falta de estructura comercial/digital para convertir visibilidad en ventas constantes; diagnosticar el funnel completo.
- UVP: no definida, a construir cruzando competencia+cliente+producto+marca.
- Cliente: hipótesis por ocasión de consumo (antojo individual, pareja, parranda, familia, reuniones, oficinas).

## FASE 2 — PROFUNDIZACIÓN ✅ (completa)
- Competencia: ver `analisis-competencia.md` (10 negocios, 3 hallazgos clave de oportunidad).
- Marca deseada: cercana, auténtica, divertida, antojadora, casual — NO gourmet. Eje: "compartir un momento".
- Ventas: hoy 100% WhatsApp manual, Sara Restrepo sola, horario 8am–5pm.
- Pagos: transferencia y efectivo, sin anticipo obligatorio; estados de pago a soportar (pendiente/por confirmar/confirmado/pagado/contra entrega).
- Domicilio y pedido mínimo: NO definidos — regla de negocio pendiente, no inventar cifras. Arquitectura con reglas configurables por zona.
- Capacidad de producción: variable, no medida — no prometer tiempos/cantidades sin datos reales. Modelo de estados de pedido + noción de saturación.
- Fidelización: no existe hoy. Funnel deseado con campos mínimos de cliente definidos. Sin CRM complejo en MVP.
- Analítica: desde cero. KPIs deseados en Marketing/Comercial/Producto/Fidelización/Operación. MVP simple → dashboard futuro.

## FASE 3 — ARQUITECTURA ✅ (completa)

### Infraestructura técnica
Dominio y hosting pendientes (desde cero). El blueprint debe evaluar/recomendar (con pros/contras/costos) dominio+alternativas, hosting, plataforma de despliegue, correo corporativo, SSL, analítica, integración WhatsApp, posibilidad futura n8n+IA. Criterios: económico, fácil de administrar, rápido, seguro, Mobile First, escalable, sin sobredimensionar el MVP.

### Modelo de mantenimiento y stack
El usuario seguirá trabajando con Claude para cambios de estructura/funcionalidades/integraciones (no depender de un desarrollador externo para eso). Sara necesita panel/CMS sencillo para editar ella misma: productos, precios, disponibilidad, fotos, promos, horarios, contacto, zonas de cobertura. Arquitectura deseada: código a la medida + CMS/panel simple (NO "arrastrar y soltar" tipo Wix, para no limitar IA/automatización futura). Evolución: MVP → Mantenimiento (Sara en panel) → Evolución (con Claude) → Escalamiento (WhatsApp, IA, n8n, BD, pedidos, fidelización, analytics, dashboard). El blueprint debe comparar alternativas de arquitectura (costo/complejidad/mantenimiento/crecimiento) y recomendar una.

### Identidad de marca — activos reales existentes (CONFIRMADO, partir de esto, no inventar una marca nueva)
- Logo real ya existe (imagen recibida): sello circular con banano/plátano animado con gorro de chef, saludando; texto perimetral "PATACONCITOS.COM" arriba y "UNA DELICIA AL PALADAR" abajo; "cuentas" de colores (verde, naranja, amarillo) simulando trozos de patacón/topping alrededor del círculo interior; dos estrellas naranjas.
- Paleta observada en el logo (para tomar como base real, no definitiva hasta profesionalizarla): azul petróleo/gris oscuro (anillo interior y fondo del sello), dorado/amarillo mostaza (anillo exterior y texto de la frase inferior), naranja (anillo intermedio y estrellas), blanco (texto "PATACONCITOS.COM" y guantes del personaje), amarillo/verde del plátano del mismo personaje.
- Cuenta de Instagram real: @pataconcitos.com_ (coincide con el nombre en el logo).
- Existen fotos/videos reales de productos publicados en redes — el usuario quiere que se usen esos activos reales en vez de fotos de banco de imágenes.
- Pendiente de profesionalizar (no existe aún como sistema): paleta oficial documentada, tipografías, estilo fotográfico consistente, iconografía, tratamiento de imágenes, aplicación consistente en web/IG/WhatsApp, posible empaque/material promocional.
- Dirección deseada: fresca, alegre, apetecible, moderna, cercana, reconocible, adaptable a redes, funcional mobile-first — conectada con las sensaciones ya definidas (antojo+sabor+cercanía+diversión+compartir+confianza). Partir del logo/mascota existente y evolucionar el sistema visual sin perder reconocimiento, no reemplazar la marca.
- El blueprint debe señalar qué contenido visual nuevo se necesitaría producir a futuro (fotos profesionales de canastas, videos verticales para reels, fotos de menú, de preparación, de entrega/experiencia) — sin asumir que ya existe.

## FASE 4 — BLUEPRINT ✅ (completo, v2.1 aprobado)
Blueprint completo generado y aprobado — ver `blueprint-pataconcitos.md`.

## FASE 5 — DISEÑO (en curso)
Ver el registro de avance y hallazgos dentro de `blueprint-pataconcitos.md` (sección "Registro de Fase 5 — Diseño") y las piezas de alta fidelidad en la carpeta `diseño/`.
