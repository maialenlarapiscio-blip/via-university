# Skills y rutina semanal

## 1. Mapa de skills: cuál usar para cada trabajo

| Trabajo | Skill | Conector |
|---|---|---|
| Planear la semana, revisar métricas | `regulars-marketing-agent` | Slack (solo lectura), FeedHive |
| Escribir cualquier texto | `regulars-content-principles` | |
| Bienvenida a nuevo partner | `regulars-new-partner-post` | Slack, Canva |
| Newsletter a clientes | `regulars-newsletter` | Brevo (borrador) |
| Kit de impresión para un local | `regulars-offline-kit` | |
| Visual con iPhone o Apple Wallet | `regulars-apple-visuals` | Canva, Figma |
| Campaña nueva (lanzamiento, ciudad nueva) | `marketing:campaign-plan` | Drive |
| Análisis de competencia | `marketing:competitive-brief` | Chrome |
| Informe mensual | `marketing:performance-report` | FeedHive |
| Revisión final antes de aprobar | `marketing:brand-review` | |
| Moodboard y referencias visuales | | Savee, Miro |

## 2. Arreglos que hay que hacer en las skills

1. **Fusionar los dos kits de impresión.** Recomendación: quedarse con `regulars-offline-kit` porque usa los scripts fijos de Hans y saca las cuatro piezas en danés e inglés. Borrar `regulars-promotional-marketing-kit` o convertirlo en la versión "editable en Canva" solo si un cliente lo pide. Así Claude nunca duda.
2. **Corregir `regulars-content-principles`.** Cambiar "Regulars Aarhus" por "Regulars" y "Aarhus" por "ciudades danesas". Decidir si Pinterest es canal o no; si no lo es, quitarlo.
3. **Quitar los datos duplicados de las skills.** Personas, competidores y cifras viven en los archivos de conocimiento. Las skills solo dicen "lee 03-audiencias.md".
4. **Mover las skills de Lupulus** a su propio proyecto.

Si quieres, Claude puede hacer estos cambios con la skill `skill-creator`. Solo dile: "aplica los arreglos de skills-y-rutina.md".

## 3. Rutina semanal (horario de 09:00 a 15:00)

| Día | Qué pasa | Quién lo dispara | Tu tiempo |
|---|---|---|---|
| Lunes 09:00 | Claude lee #gtm-csm, detecta partners nuevos, te deja la lista de ideas y las preguntas para el equipo. | Tarea programada | 20 min |
| Martes | Plan de la semana y borradores de captions. | Tú abres el chat | 45 min |
| Miércoles | Visuales en Canva. | Tú | 60 min |
| Jueves | Feedback, `brand-review`, apruebas y programas en FeedHive. | Tú | 30 min |
| Viernes 14:00 | Claude te pide los datos de Instagram, LinkedIn y demos, y escribe qué funcionó y qué cambiar. | Tarea programada | 15 min |
| Primer lunes del mes | Análisis de competencia y informe mensual. | Tarea programada | 30 min |

## 4. Tareas programadas para crear

Escribe esto en un chat del proyecto para que Claude las cree:

1. **Lunes 08:47, Regulars recogida semanal**: "Ejecuta el paso 1 de regulars-marketing-agent. Lee #gtm-csm de los últimos 7 días, lista partners nuevos, prepara las preguntas para el equipo y actualiza el tablero de contenido."
2. **Viernes 13:52, Regulars revisión semanal**: "Ejecuta el paso 5 de regulars-marketing-agent. Pídeme los datos, compáralos con 05-resultados.md y propón dos cambios para la semana que viene."
3. **Primer lunes del mes 10:13, Regulars mes**: "Ejecuta marketing:competitive-brief para MyLoyal, MitStempel y BakerPoints y marketing:performance-report del mes anterior. Actualiza 04-competencia.md y 05-resultados.md."

Las horas no están en punto a propósito: así no coinciden con el pico de uso y no se retrasan.

## 5. Tablero de contenido

Un artifact con base de datos, visible desde el móvil. Columnas: título, persona, pilar, canal, formato, fecha, CTA, etapa, link. Para crearlo, escribe en el proyecto: "Crea el tablero de contenido de Regulars".
