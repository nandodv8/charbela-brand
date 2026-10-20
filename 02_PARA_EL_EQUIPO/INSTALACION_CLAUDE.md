# Instalación en una computadora nueva

Unos 15 minutos. Hazlo en este orden.

> Los nombres exactos de los menús de Claude cambian entre versiones. Si algo no se llama igual en tu pantalla, busca la sección equivalente; los pasos de fondo son los mismos.

---

## 1 · Copiar la carpeta

Copia `CHARBELA_BRAND_OS` completa a la computadora nueva. Un lugar razonable:

```
Documentos\CHARBELA_BRAND_OS\
```

No la dejes en Descargas ni en el escritorio: esto se consulta durante meses.

---

## 2 · Instalar la tipografía

1. Entra a `05_MARCA/tipografia/estaticas/`.
2. Selecciona los seis archivos `.ttf`.
3. Clic derecho → **Instalar para todos los usuarios** (en Windows) o doble clic → Instalar (en Mac).

Parkinsans tiene licencia abierta (SIL Open Font License, incluida en la carpeta): se puede instalar en todas las computadoras del negocio, usar en la web y cargar en Canva sin pagar nada.

Para la web y el CRM está también `variable/Parkinsans-VariableFont_wght.woff2`, que es el formato que pide `brand.css`.

---

## 3 · Crear el proyecto en Claude

1. En Claude, crea un proyecto y llámalo **Charbela**.
2. Abre `01_DOCS/INSTRUCCIONES_PROYECTO.md`, copia el bloque que está bajo el título **BLOQUE PARA PEGAR** y pégalo en las instrucciones del proyecto.
3. Sube al conocimiento del proyecto estos dos archivos:
   - `01_DOCS/BRAND.md`
   - `01_DOCS/MICROCOPY.md`

Con eso, Claude ya conoce la marca en cada conversación de ese proyecto, sin que nadie se la explique.

---

## 4 · Instalar las cinco skills

Las skills son las ayudas para las tareas de todos los días: posts, WhatsApp, descripciones, revisión.

En la configuración de Claude, en la sección de **capacidades o skills**, agrega cada una. Según la versión, se carga la carpeta o el archivo comprimido:

| Skill | Carpeta | Comprimido |
|---|---|---|
| charbela-voz | `03_SKILLS/charbela-voz/` | `03_SKILLS/_zips/charbela-voz.zip` |
| charbela-post | `03_SKILLS/charbela-post/` | `_zips/charbela-post.zip` |
| charbela-whatsapp | `03_SKILLS/charbela-whatsapp/` | `_zips/charbela-whatsapp.zip` |
| charbela-producto | `03_SKILLS/charbela-producto/` | `_zips/charbela-producto.zip` |
| charbela-revision | `03_SKILLS/charbela-revision/` | `_zips/charbela-revision.zip` |

**Si esta versión de Claude no permite instalar skills:** no pasa nada. Sube los cinco archivos `SKILL.md` al conocimiento del proyecto, igual que `BRAND.md`. Funcionan casi igual, solo que Claude no las elige sola: hay que decirle "usa la guía de WhatsApp", por ejemplo.

---

## 5 · Probar que quedó bien

Abre una conversación nueva en el proyecto y escribe:

> Una clienta pregunta por bocaditos para una primera comunión de 40 personas. ¿Cómo le contesto?

Quedó bien instalado si la respuesta:

- Es cálida pero **sin bromas** sobre antojos ni culpa (es un evento religioso).
- Pregunta la fecha en lugar de inventarla.
- **No pone un precio.** Debe dejar algo como `[FALTA: precio]` o preguntarlo.

Si te responde con humor de antojo o con un precio inventado, algo no cargó. Revisa que las instrucciones del proyecto estén pegadas y que `BRAND.md` esté subido.

---

## 6 · Si además vas a tocar el CRM o la web

Sigue `04_TOKENS/INTEGRACION_CRM.md`. Eso es trabajo de quien programa, no del equipo de pastelería.

---

## Qué hacer cuando algo cambie

Si cambia un precio, un teléfono o una regla de marca, **se actualiza `01_DOCS/BRAND.md` y se vuelve a subir al proyecto.** No se corrige solo en una conversación: lo que se dice en un chat se olvida, lo que está en `BRAND.md` lo lee Claude siempre.
