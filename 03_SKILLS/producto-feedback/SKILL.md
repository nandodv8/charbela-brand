---
name: producto-feedback-charbela
description: Habilidad para reportar bugs, sugerir adecuaciones, pulido visual de la interfaz y nuevas funcionalidades en el CRM Charbela conectando directamente con el panel vibe_feedback.
---

# 🛠️ Habilidad: Pulido, Mejoras y Bugs del CRM (Vibe Feedback)

Esta habilidad conecta al agente con el backlog tecnológico de la aplicación web de Charbela CRM. Permite que cualquier sugerencia de Gladys, Fernando o Charbela durante una conversación quede automáticamente registrada en el sistema de desarrollo.

---

## 📌 1. Ciclo de Vida de Mejoras y Bugs

Las solicitudes se clasifican en:
- `tipo`:
  - `bug`: Error que impide realizar una acción o rompe la interfaz.
  - `mejora`: Optimización de un flujo existente (ej. menos clics, carga más rápida).
  - `adecuacion`: Ajuste a un proceso de negocio o nueva necesidad de pastelería.
  - `pulido`: Detalles visuales, colores, tipografía, espaciado o redacción.
- `prioridad`: `baja`, `media`, `alta`, `critica`.
- `estado`: `pendiente`, `en_progreso`, `resuelto`, `descartado`.

---

## 🛠️ 2. Herramientas MCP Disponibles

1. `reportar_mejora_o_bug`:
   - Crea un registro en la colección `vibe_feedback` de Firestore.
   - Parámetros: `titulo`, `descripcion`, `modulo` (`Ventas`, `Obrador`, `Personal`, `Finanzas`, `Calidad`, `General`), `tipo`, `gravedad`, `capturaBase64` o `capturaUrl`.
   - Si se proporciona captura o imagen de soporte, se sube automáticamente a `vibe_feedback_screenshots/` y se enlaza como `screenshotUrl`.
   - Aparece de inmediato en el botón flotante de retroalimentación dentro de la web app con su captura visible.

2. `adjuntar_captura_mejora_bug`:
   - Permite adjuntar una captura de pantalla o mockup a un reporte existente mediante `feedbackId` y `capturaBase64` o `capturaUrl`.

3. `consultar_mejoras_y_bugs`:
   - Consulta el listado de tareas pendientes o en desarrollo por módulo.

4. `actualizar_estado_mejora_bug`:
   - Cambia el estado a `resuelto` o añade notas técnicas cuando el desarrollador completa la tarea.

5. `generar_enlace_crm`:
   - Devuelve el link directo y parametrizado para cualquier pantalla o pedido del CRM.
