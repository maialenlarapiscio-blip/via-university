# Regulars: Marketing and Brand HQ

Estructura de trabajo para el proyecto de Claude (Cowork) de Regulars. Objetivo: que Claude funcione como tu equipo de marketing y branding, y tú como Head of Marketing and Brand que decide y aprueba.

## 1. Diagnóstico: por qué se siente desordenado

1. **Dos skills hacen lo mismo.** `regulars-offline-kit` (PDFs con los scripts de Hans) y `regulars-promotional-marketing-kit` (plantillas en Canva) crean el mismo kit de impresión. Claude no sabe cuál usar y tú tampoco.
2. **Las skills se contradicen.** `regulars-content-principles` habla de "Regulars Aarhus", solo Aarhus y con Pinterest. `regulars-marketing-agent` habla de toda Dinamarca y no menciona Pinterest. Cada chat sale distinto según qué skill cargue.
3. **No hay una fuente única de verdad.** Datos de marca, cifras aprobadas, personas y competidores viven dentro de varias skills y de un Claude Doc. Si algo cambia, hay que editarlo en cinco sitios.
4. **Lupulus está mezclado con Regulars.** Las skills de Lupulus viven en la misma cuenta. Si trabajas Lupulus dentro del proyecto Regulars, el tono se contamina.
5. **La rutina semanal existe en papel, pero nadie la dispara.** El lunes de recogida y el viernes de métricas dependen de que tú te acuerdes.
6. **No hay un tablero de contenido.** Las piezas no tienen un sitio donde ver su estado (idea, borrador, revisión, aprobado, publicado).

## 2. Lo que Claude ya puede hacer hoy y casi no estás usando

| Función | Para qué te sirve en Regulars |
|---|---|
| **Proyectos de Cowork** | Un espacio fijo con instrucciones, archivos y el historial de tareas. Todo chat de Regulars empieza sabiendo quién es la marca. |
| **Tareas programadas** | Claude arranca solo la rutina del lunes, el control de métricas del viernes y el análisis mensual de competencia. |
| **Skills** | Recetas fijas para trabajos que repites: post de nuevo partner, newsletter, kit de impresión. |
| **Conectores** | Slack (leer #gtm-csm), Canva (visuales), FeedHive (programar), Brevo (newsletter), Drive, Gmail, Calendar, Savee (moodboards), Figma y Miro. |
| **Plugin de marketing** | `campaign-plan`, `competitive-brief`, `performance-report`, `brand-review`. Ya están instalados y no los estás usando. |
| **Artifacts con base de datos** | Un tablero de contenido vivo que Claude actualiza y tú ves desde el móvil. |
| **Claude Docs** | Documentos que siguen vivos (playbook, brief de campaña) en vez de respuestas que se pierden en el chat. |
| **Memoria** | Claude recuerda tus preferencias y decisiones entre chats. |
| **Claude en Chrome y computer use** | Revisar los perfiles de competidores o subir cosas en webs donde no hay conector. |

## 3. La estructura nueva

### 3.1 Dos proyectos, no uno
1. **Regulars HQ**: todo lo de Regulars.
2. **Lupulus**: sus tres skills y su propia guía. Nunca se mezclan.

### 3.2 Dentro de Regulars HQ
1. **Instrucciones del proyecto**: pega el texto de `instrucciones-proyecto.md`.
2. **Archivos de conocimiento** (carpeta `brain/` (el Regulars Brain)), la fuente única de verdad:
   1. `01-marca.md`: voz, tono, reglas visuales, reglas Apple.
   2. `02-datos-aprobados.md`: cada cifra con su estado (confirmada o pendiente).
   3. `03-audiencias.md`: las personas a las que escribimos.
   4. `04-competencia.md`: competidores y nuestra posición.
   5. `05-resultados.md`: línea base y aprendizajes semanales.
3. **Skills**: ver `skills-y-rutina.md` para qué skill usar en cada trabajo y qué arreglar.
4. **Tareas programadas**: la rutina semanal automática, también en `skills-y-rutina.md`.
5. **Tablero de contenido**: un solo artifact con base de datos donde vive cada pieza y su estado.

### 3.3 Cómo nombrar los chats
Así encuentras todo rápido desde el historial:

`[Canal] Tipo · Tema · Fecha`

Ejemplos: `[IG] Welcome · Café Aura · 10 nov`, `[NL] Newsletter noviembre`, `[KIT] Offline · Støvring Pizza`, `[STRAT] Plan Q1`.

### 3.4 Roles
| Rol | Quién | Qué hace |
|---|---|---|
| Head of Marketing and Brand | Tú | Define prioridades, aprueba, programa en FeedHive, habla con Alexander y Hans. |
| Estratega | Claude | Plan semanal y trimestral, campañas, posicionamiento. |
| Copywriter | Claude | Captions, newsletter, guiones de reels, en inglés y danés con traducción. |
| Diseño | Claude + Canva | Visuales de partner, kits de impresión, carruseles. |
| Analista | Claude | Métricas del viernes, competencia mensual, informe mensual. |
| Fuente de datos | Alexander, Hans, equipo CSM | Confirman cifras, resultados de clientes, novedades de producto. |

## 4. Plan de 30 días para dejarlo funcionando

| Semana | Qué hacemos | Resultado |
|---|---|---|
| 1 | Crear los dos proyectos, pegar instrucciones, subir los 5 archivos de conocimiento. Rellenar los huecos marcados con [ ]. | Claude responde igual en cualquier chat. |
| 1 | Arreglar las skills (fusionar los kits, quitar "solo Aarhus"). | Cero contradicciones. |
| 2 | Crear el tablero de contenido y las tareas programadas. | La rutina corre sola. |
| 2 | Pedir a Alexander que confirme las cifras de la web. | Podemos usar números reales en los posts. |
| 3 | Primer `competitive-brief` completo y primer plan de campaña con `campaign-plan`. | Posicionamiento claro frente a MyLoyal, MitStempel y BakerPoints. |
| 4 | Primer informe mensual con `performance-report`. | Sabemos qué funciona y qué cortar. |

## 5. Cómo empezar ahora mismo
1. Crea el proyecto **Regulars HQ** en Claude.
2. Pega `instrucciones-proyecto.md` en las instrucciones del proyecto.
3. Sube la carpeta `brain/` (el Regulars Brain) y rellena los [ ] con tu equipo.
4. Abre un chat dentro del proyecto y escribe: "Configura las tareas programadas de skills-y-rutina.md".
