# CHARBELA BRAND OS

Sistema de marca operativo de Charbela Pastelería. Todo lo necesario para que la marca nueva se aplique igual en cualquier computadora, con o sin diseñador.

**Versión 1.0 · 12 de octubre de 2026**

---

## Empieza según quién eres

| Si eres… | Abre esto |
|---|---|
| **Charbela o Gladys** | `02_PARA_EL_EQUIPO/GUIA_CHARBELA_Y_GLADYS.md` — una página, en lenguaje llano |
| **Quien instala en una PC nueva** | `02_PARA_EL_EQUIPO/INSTALACION_CLAUDE.md` — 15 minutos |
| **Quien escribe o revisa textos** | `01_DOCS/BRAND.md` §7 (voz) y §8 (diccionario) |
| **Quien diseña una pieza** | `01_DOCS/BRAND.md` §3, §4, §5 + `05_MARCA/` |
| **Quien programa el CRM o la web** | `04_TOKENS/INTEGRACION_CRM.md` |
| **Quien manda algo a imprenta** | `01_DOCS/BRAND.md` §13 (checklist) y §14 (pendientes) + `07_EDITABLES/` |
| **Quien edita una pieza en Illustrator** | `07_EDITABLES/` — y antes, `01_DOCS/BRAND.md` §14-A |

---

## Qué hay dentro

```
CHARBELA_BRAND_OS/
├── README.md                      ← este archivo
├── VERSION.txt
│
├── 01_DOCS/                       La fuente de verdad
│   ├── BRAND.md                   Sistema completo: marca, color, voz, pilares, canales
│   ├── MICROCOPY.md               Textos de cara al cliente (portal + WhatsApp)
│   └── INSTRUCCIONES_PROYECTO.md  Bloque para pegar en el proyecto de Claude
│
├── 02_PARA_EL_EQUIPO/
│   ├── GUIA_CHARBELA_Y_GLADYS.md  Cómo pedirle cosas a Claude
│   └── INSTALACION_CLAUDE.md      Puesta en marcha en una PC nueva
│
├── 03_SKILLS/                     Cinco ayudas para las tareas diarias
│   ├── charbela-voz/
│   ├── charbela-post/
│   ├── charbela-whatsapp/
│   ├── charbela-producto/
│   ├── charbela-revision/
│   └── _zips/                     Las mismas, comprimidas para instalar
│
├── 04_TOKENS/                     Para código
│   ├── brand-tokens.json
│   ├── brand.css
│   └── INTEGRACION_CRM.md
│
├── 05_MARCA/                       Assets de uso diario
│   ├── brandbook/                 El brandbook completo (PDF, 61 pp.)
│   ├── logotipo/                  2 estructuras × 3 colores, en svg y png
│   ├── tipografia/                Parkinsans: variable, estáticas, woff2, licencia
│   ├── cromatica/                 Cartas de color RGB y CMYK
│   ├── recursos-graficos/         16 elementos del sistema (svg y png)
│   └── highlights-instagram/      6 íconos de destacados
│
├── 06_REFERENCIA/
│   ├── ejemplos-posteos/          7 posteos de muestra del estudio
│   └── FUENTES_ORIGINALES.md      Dónde está lo que no entró aquí
│
└── 07_EDITABLES/        182 MB    Archivos .ai — requieren Adobe Illustrator
    ├── sistema/                   Logotipo, cromática, recursos gráficos
    ├── piezas-digitales/          Ejemplos de posteos, highlights de Instagram
    └── piezas-fisicas/            Caja, fajín, funda, stickers, menú, catálogo,
                                   mandil, camiseta, gorra, letrero, tarjeta de fidelidad
```

---

## Dos versiones de esta carpeta

| Versión | Peso | Para qué |
|---|---|---|
| **Completa** (con `07_EDITABLES/`) | 254 MB | La computadora donde se diseña o se prepara material para imprenta |
| **Ligera** (sin `07_EDITABLES/`) | 68 MB | Las demás: equipo, Claude, CRM. Se copia y se manda sin fricción |

Los ZIP de ambas están junto a esta carpeta: `CHARBELA_BRAND_OS.zip` y `CHARBELA_BRAND_OS_LIGERO.zip`.

### Antes de abrir un `.ai`

1. **Instala la tipografía primero** (`05_MARCA/tipografia/estaticas/`). Si Parkinsans no está instalada, Illustrator sustituye la fuente y los textos se descuadran sin avisar.
2. Si al abrir pide imágenes enlazadas, hay que localizarlas: el paquete del estudio no trae una carpeta de imágenes aparte.
3. **Las iteraciones con el estudio están agotadas.** Antes de modificar una pieza entregada, lee `01_DOCS/BRAND.md` §14-A: hay una consulta pendiente sobre plantillas editables y límites de derivación. Guarda siempre con nombre nuevo; no sobreescribas el original.

---

## Las cinco reglas que valen para todo

1. **Dos vías, una marca.** Antojo (Bakes) y celebración (eventos) se dicen distinto. Antes de escribir o diseñar, define cuál es.
2. **El texto es café `#5C3339` sobre beige `#FCFBF0`.** Cuando dudes, ese par.
3. **El naranja `#F9603D` nunca es texto.** Es acento, y menos del 15% de la pieza.
4. **Una sola tipografía: Parkinsans.**
5. **Nunca se inventa un dato.** Precios, teléfonos, horarios, plazos, mínimos, porciones, alérgenos: si no está confirmado, no se escribe.

---

## Qué no está resuelto todavía

El sistema tiene campos marcados `⬜` a propósito. No se rellenan a mano ni se inventan: se resuelven y se actualiza `BRAND.md`.

Los principales: el año de origen (hay dos cifras circulando: 12 y 14 años), el teléfono oficial único, el horario de atención, la mecánica de la tarjeta de fidelidad, la fecha del corte visible y el dominio definitivo. Lista completa en `01_DOCS/BRAND.md` §11 y §14.

También hay tres cosas que **no se comunican todavía**: la línea de cafetería (café, lattes, matcha), la isla o local físico, y la dirección del taller.

---

## Cómo se mantiene

Este kit es una copia. Si cambia una regla de marca:

1. Se actualiza `01_DOCS/BRAND.md` primero, con fecha.
2. Después el código, las skills y las piezas.
3. Se sube el número de versión en `VERSION.txt` y se vuelve a exportar la carpeta.

El orden importa: si una pieza cambia antes que el documento, en dos meses nadie sabe cuál es la regla.
