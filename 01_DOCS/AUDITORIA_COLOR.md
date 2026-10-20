# Auditoría de color del material de Polen

> **2026-10-12** · Verificación técnica de los códigos de color del entregable, de los SVG y de la coherencia entre documentos.
> Método: comparación HEX↔RGB declarados, extracción de todos los colores de los 36 SVG entregados y cálculo de diferencia perceptual **ΔE (CIE76)** contra la paleta oficial.

---

## Resumen

| Qué se revisó | Resultado |
|---|---|
| Consistencia HEX ↔ RGB de los 6 colores | ✅ Correcta en los seis |
| Logotipo (6 SVG) | ✅ Impecable: un color de paleta exacto por archivo |
| Página de variantes del brandbook vs cartas de color | 🔴 **Se contradicen** |
| Recursos gráficos y highlights (36 SVG) | 🟡 45 colores fuera de paleta en 76 de 107 usos |
| Equivalencia Pantone / tinta plana | 🔴 **No existe en el entregable** |
| Conversión CMYK ↔ RGB | ⚪ No verificable sin perfil ICC (ver abajo) |

---

## 🔴 1. El brandbook y las cartas de color no dicen lo mismo

En la página de cromática del **brandbook** (`CHARBELA_TIERRA_AP_V3.pdf`), los chips "CAFÉ VARIANTE" y "ROSA VARIANTE" muestran estos códigos:

```
CAFÉ VARIANTE      ROSA VARIANTE
CMYK 44, 80, 60, 45    CMYK 0, 39, 0, 0
RGB  92, 51, 57        RGB  246, 179, 217
HEX  #5C3339           HEX  #F6B3D9
```

Son **exactamente los valores de los colores base**, no de las variantes. En las cartas de color (`Cromática RGB_Charbela_AP.pdf` y `Cromática CMYK_Charbela_AP.pdf`) las mismas variantes aparecen con valores distintos:

```
CAFÉ VARIANTE      ROSA VARIANTE
CMYK 50, 78, 63, 62    CMYK 4, 47, 0, 0
RGB  71, 36, 41        RGB  237, 157, 202
HEX  #472429           HEX  #ED9DCA
```

Es un error de maquetación del brandbook: los códigos quedaron copiados del bloque base, aunque el swatch impreso sí muestra un tono más oscuro.

**Qué hacemos:** `BRAND.md` y `brand-tokens.json` toman como válidos **los valores de las cartas de color** (`#472429` y `#ED9DCA`), porque son los documentos específicos de cromática y porque coinciden con lo que el swatch muestra. Entra en la consulta al estudio para confirmación formal.

**Por qué importa:** quien lea solo el brandbook creerá que las variantes no existen y usará dos veces el mismo color. Y el café variante es justamente el mejor color de texto del sistema: 13:1 de contraste sobre beige.

---

## 🔴 2. No hay equivalencia Pantone ni de tinta plana

El entregable trae CMYK, RGB y HEX. No trae Pantone ni referencia de tinta plana para ningún color.

Esto no afecta nada digital, pero sí todo lo que se fabrica con proveedores distintos:

| Trabajo | Problema sin Pantone |
|---|---|
| Letrero corpóreo y vinilo | El rotulista elige el tono "más parecido" de su catálogo |
| Bordado de mandiles, camisetas y gorras | El hilo se elige por carta de hilos, no por CMYK |
| Caja y funda a tinta plana | Cada imprenta interpreta el rosa a su manera |
| Lotes distintos del mismo empaque | Sin referencia fija, el rosa deriva entre tiradas |

El rosa es el color patrimonial de la marca y el que más se va a reproducir. Es el que más necesita una referencia fija.

**Qué hacemos:** pedirlo al estudio (está en `BRAND.md` §14-A). Si no lo entregan, la alternativa es una **prueba de color impresa** con una imprenta de confianza y fijar nosotros el Pantone más cercano, dejándolo escrito en `BRAND.md`.

---

## 🟡 3. Los SVG de recursos gráficos tienen deriva de color

De los 36 SVG de recursos gráficos y highlights:

- **49 colores distintos** en total.
- **45 están fuera de la paleta oficial**, en **76 de 107 usos**.

Clasificados por diferencia perceptual contra el color de paleta más cercano:

| Rango ΔE | Casos | Lectura |
|---|---|---|
| < 1.5 (imperceptible) | 17 colores | Deriva de exportación. El ojo no lo distingue |
| 1.5 – 3.5 (visible) | 12 colores | Se nota si están lado a lado |
| 3.5 – 6 (notoria) | 13 colores | Se nota sin comparar |
| > 6 (otro color) | 3 colores | Decisión de diseño o error claro |

Los casos que más importan:

| Color | Usos | Más cercano | ΔE |
|---|---|---|---|
| `#EDECE2` | 11 | Beige Evento `#FCFBF0` | 5.22 |
| `#EFEEE3` | 4 | Beige Evento | 4.52 |
| `#F4AAD5` | 3 | Rosa Antojo `#F6B3D9` | 4.36 |
| `#5C2F32` | 3 | Café Choco `#5C3339` | 3.56 |
| `#5F3436` | 3 | Café Choco | 3.00 |

`#EDECE2` con once usos es, en la práctica, un **quinto color operando en el sistema sin estar declarado**: un beige más gris que el Beige Evento oficial.

**Causa probable:** round-trip de perfil de color al exportar de Illustrator (documento en CMYK exportado a SVG, que es RGB), más trazados reutilizados de versiones anteriores. Es deriva técnica, no decisión estética — en una ilustración plana, una sombra intencional estaría a ΔE 10 o más, no a 3.

### Qué hice

Generé una versión normalizada, **sin tocar los originales**:

```
05_MARCA/recursos-graficos/svg/               ← originales del estudio, intactos
05_MARCA/recursos-graficos/svg-normalizado/   ← 30 archivos con la paleta exacta
05_MARCA/highlights-instagram/                ← originales
05_MARCA/highlights-instagram/svg-normalizado/ ← 6 archivos
```

Regla aplicada: todo color a **ΔE ≤ 6** del color de paleta más cercano se reemplaza por ese color. 42 reemplazos en 36 archivos.

Tres colores quedaron **sin tocar** porque están demasiado lejos para decidirlo automáticamente:

| Color | Más cercano | ΔE | Comentario |
|---|---|---|---|
| `#F9B4CE` | Rosa Antojo | 6.43 | Rosa que se va al salmón |
| `#FBB5CF` | Rosa Antojo | 6.57 | Igual |
| `#521E26` | Café Variante | 8.43 | Café más oscuro y violáceo, en un highlight |

Esos tres hay que mirarlos a ojo y decidir: o son un acento deliberado del ilustrador —y entonces deberían estar declarados en la paleta— o son un error y se corrigen.

**Cuál usar:** para piezas nuevas, la carpeta `svg-normalizado`. Los originales se conservan como entregable del estudio y como referencia si algún día hay que discutir una pieza con ellos.

---

## ⚪ 4. Lo que no se puede verificar sin perfil de color

Los seis colores declaran CMYK y RGB. Comprobar si esa conversión es correcta requiere saber **con qué perfil ICC se hizo** (US Web Coated, FOGRA, otro): la misma mezcla CMYK da valores RGB distintos según el perfil, y una conversión aritmética simple no sirve como prueba. No hay perfil declarado en el entregable.

Hay además un punto técnico esperable: **Naranja Metiche `#F9603D` es un naranja muy saturado que no existe en CMYK.** Impreso en `0, 82, 85, 0` se va a ver más apagado y más rojizo que en pantalla. No es un error del estudio —es el límite físico de la tinta—, pero sí una expectativa que conviene manejar antes de ver la primera caja impresa, porque ese naranja es el "stopper visual" de todo el sistema.

**Verificación propuesta:** una prueba de color impresa de la caja o del fajín antes de la tirada completa. Es el único modo de saber cómo se ve de verdad, y cuesta mucho menos que un lote de mil cajas.

---

## Reglas que salen de esta auditoría

1. **El color se toma de `brand-tokens.json` o de las cartas de color. Nunca con cuentagotas sobre un recurso gráfico ni sobre un PNG.** Es así como `#EDECE2` llegó a once archivos.
2. **Tolerancia:** ΔE ≤ 1.5 se acepta como deriva de exportación. Por encima de 2 se corrige.
3. **Para piezas nuevas**, usar `svg-normalizado`.
4. **Antes de cualquier tirada grande**, prueba de color impresa.
5. **Antes de bordado, vinilo o corpóreo**, resolver el Pantone.
