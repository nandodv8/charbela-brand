# Integración de tokens en el CRM y la tienda

Para quien programa. Objetivo: que el color y la tipografía del sistema vivan en un solo lugar y que el corte visual se pueda hacer y revertir en un commit.

---

## Qué hay aquí

| Archivo | Qué es |
|---|---|
| `brand-tokens.json` | Paleta, contrastes verificados, tipografía, voz, pilares y datos maestros en estructura consumible por código y por agentes |
| `brand.css` | Variables CSS `--cb-*`, roles semánticos, clases de vía, modo oscuro y un bloque de mapeo a las variables que el CRM ya usa |

---

## Instalación en `crm-charbela`

**1 · Fuente**

```
cp ../05_MARCA/tipografia/variable/Parkinsans-VariableFont_wght.woff2  public/fonts/
cp ../05_MARCA/tipografia/variable/Parkinsans-VariableFont_wght.ttf    public/fonts/
```

El `@font-face` de `brand.css` apunta a `/fonts/`.

**2 · CSS**

```
cp brand.css src/brand.css
```

En `src/main.jsx`, importar **antes** de `index.css`:

```js
import './brand.css'
import './index.css'
```

El orden importa: `brand.css` declara los tokens y luego remapea las variables existentes; `index.css` ya no necesita cambios para el corte.

**3 · Verificación**

```
npm run dev
```

Revisar en este orden, que es el de impacto sobre el cliente:

1. `/c/:id` — portal de cotización (lo ve el cliente)
2. `/tienda` y `/cotizar` — tienda y intake
3. `/` — dashboard
4. `/ventas`, `/produccion`, `/finanzas` — operación interna
5. Modo oscuro, si está activo en el equipo

**4 · Revertir**

Quitar el import de `brand.css`. Nada más. El bloque de mapeo es lo único que altera la apariencia existente, y vive en ese archivo.

---

## Las decisiones que vas a notar

**El botón primario es café, no rosa.** `--color-primary` queda mapeado a `--cb-action`, que es Café Choco Chips. El motivo es medible: blanco sobre Rosa Antojo da 1.70:1 de contraste, muy por debajo del mínimo legible. El rosa queda como superficie de marca, que es su rol en el brandbook.

**El naranja no es color de texto ni de estado.** Naranja sobre beige da 2.98:1: falla incluso como texto grande. Está disponible como `--cb-accent` para superficies, badges e iconos. Si necesitas el acento *como texto*, usa `--cb-accent-text` (`#BB4B36`).

**Los estados conservan semántica propia.** `success`, `warning` y `danger` no usan la paleta de marca: el naranja es color de deseo, no de error. Un error en naranja de marca enseña al usuario que el acento significa peligro.

**Las clases de vía cambian el fondo y la presencia del acento:**

```jsx
<div className="via-celebracion">  {/* portal, cotización, documentos */}
<div className="via-bakes">        {/* tienda, catálogo retail */}
```

**Los tintes `--cb-ui-*` son derivados de interfaz**, no colores de marca. Sirven para bordes, fondos hundidos y estados hover. No se usan en piezas gráficas ni impresas.

---

## Migración por fases, cuando haya tiempo

El bloque `[MAPEO CRM]` de `brand.css` existe para no refactorizar 21 componentes el primer día. La ruta limpia:

1. Reemplazar `var(--color-*)` por `var(--cb-*)` componente por componente.
2. Cuando no queden referencias a `--color-*`, borrar el bloque de mapeo.
3. Revisar `index.css`: los sombreados y el *glass* siguen siendo de la etapa anterior y conviene reafinarlos contra el fondo beige.

---

## Pendientes conocidos

- `⬜` **Tienda web:** su microcopy sigue en la voz anterior. Es vía Bakes, registro A, y no está cubierto por `MICROCOPY.md`.
- `⬜` **`ReceiptTicket`:** la etiqueta de pedido y conservación debería rediseñarse con la identidad nueva. Es la pieza impresa que más circula.
- `⬜` **Correos transaccionales**, si existen.
- `⬜` **Séptima plantilla de WhatsApp**: mensaje de incidente (retraso o error). La estructura está en la skill `charbela-whatsapp`.
- `⬜` **Nota de conservación automática** en la plantilla "En camino": el dato ya existe por producto.

---

## Qué ya está aplicado

El microcopy del portal de cotización y las seis plantillas de WhatsApp están en voz nueva, en:

- `src/pages/ClientQuote.jsx` — 39 textos
- `src/components/WhatsAppTemplatesModal.jsx` — 12 textos

El mapeo completo, antes y después, está en `01_DOCS/MICROCOPY.md`. Si alguien pregunta por qué cambió un texto, la respuesta está ahí y no en el historial de git.
