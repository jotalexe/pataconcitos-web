# 🍌 Pataconcitos — MVP Web

Sitio MVP de **Pataconcitos**, negocio de patacones a domicilio en Medellín y Envigado (Colombia). Construido con El Arquitecto (Claude) siguiendo un proceso de descubrimiento → blueprint → diseño → construcción, documentado completo en `/docs`.

**⚠️ Estado: MVP.** El menú, los precios, la tarifa de domicilio y el pedido mínimo todavía están pendientes de definir con el negocio — se muestran honestamente marcados como pendientes en el sitio, no inventados.

## 🔗 Sitio en vivo

Una vez activado GitHub Pages en este repositorio (Settings → Pages → Branch: `main` → carpeta `/ (root)`), el sitio queda disponible en:

```
https://<tu-usuario>.github.io/pataconcitos-web/
```

## 📁 Estructura

```
index.html              → El sitio (una sola página, navegación real, WhatsApp funcional)
docs/
  blueprint-pataconcitos.md     → Documento maestro del proyecto (16 secciones)
  analisis-competencia.md       → Investigación de 10 competidores en Medellín/Envigado
  entrevista-arquitecto.md      → Notas de la entrevista de descubrimiento
  diseno/                        → Las 10 piezas de diseño de alta fidelidad (revisión, no el sitio final)
```

## 🛠 Stack

Un solo archivo HTML/CSS/JS sin dependencias de build — abre directo en cualquier navegador o se sirve tal cual con GitHub Pages, Netlify o Vercel. Fuentes desde Google Fonts (Baloo 2 + Nunito Sans).

## 📞 Contacto real usado en el sitio

- WhatsApp: `+57 300 737 4615` — **verificar que sea el número correcto antes de compartir el sitio públicamente.**
- Instagram: [@pataconcitos.com_](https://instagram.com/pataconcitos.com_)

## 🚧 Pendiente antes de un lanzamiento real

Ver la sección "Decisiones pendientes" en `docs/blueprint-pataconcitos.md` — principalmente: menú y precios definitivos, tarifa de domicilio, pedido mínimo, dominio propio (`pataconcitos.com` o similar).
