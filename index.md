---
layout: post
title: "Post-mortem: la caída de conversión en el onboarding de Nimbus"
date: 2026-07-10
categories: [post-mortem, comunicacion, trabajo-en-equipo]
---

<!--
Nota para Jorge: este front matter (las líneas entre los ---) es el formato
estándar de Jekyll, el motor que usa GitHub Pages por defecto. Si tu repo
ya tiene una estructura de _posts, este archivo debería llamarse
2026-07-10-nimbus-post-mortem-onboarding.md y vivir en esa carpeta. Si
publicás distinto (una sola página, otro generador), avisame y ajustamos
el encabezado o lo sacamos directamente.
-->

*Nota: Nimbus es un producto y un equipo ficticios, creados como caso de estudio para la Diplomatura en Mentalidad de Crecimiento y Comunicación en Entornos Digitales de Coderhouse.*

# Contexto

Nimbus es una plataforma SaaS de gestión de tareas pensada para equipos pequeños. El equipo de producto detrás de esta funcionalidad está compuesto por cuatro personas:

| Integrante | Rol |
|---|---|
| Martín | Líder técnico |
| Valentina | Diseñadora UX |
| Tomás | Desarrollador |
| Ariadna | Desarrolladora |

Durante la semana previa a un release programado, Valentina corrió un test de usabilidad sobre el formulario de onboarding. Detectó que la cantidad de campos solicitados antes de que el usuario percibiera valor generaba abandono: varios participantes dejaban el flujo antes de completar el registro. A partir de ese hallazgo, Martín decidió simplificar el formulario, eliminando dos campos opcionales y moviendo uno a un paso posterior.

Participé en este caso como facilitador neutral de la reunión de post-mortem convocada el lunes siguiente, sin responsabilidad directa en la implementación del cambio. Mi rol fue conducir la conversación con foco en el proceso y no en las personas involucradas.

# Problema

El cambio de diseño aprobado no llegó a implementarse en el release del fin de semana. Martín comunicó el pedido a Tomás por un mensaje directo de Slack un viernes a la tarde. El mensaje no incluía un plazo explícito ni quedó reflejado en el board del sprint. Tomás respondió con un emoji de confirmación y continuó con las tareas que sí tenía asignadas de forma visible, por lo que interpretó el pedido como algo sin urgencia inmediata.

El release salió el lunes con la versión anterior del formulario. Esa misma mañana, Ariadna revisó el dashboard de analytics y detectó una caída marcada en la conversión del onboarding durante el fin de semana.

| Métrica | Valor previo | Valor durante el incidente | Variación |
|---|---|---|---|
| Conversión del onboarding | 18% | 9% | -9 puntos porcentuales (-50%) |

# Acciones

## Cronología del incidente

| Momento | Evento |
|---|---|
| Viernes, 15:40 hs | Martín pide el cambio a Tomás por Slack, sin ticket ni plazo. |
| Viernes, 16:15 hs | Tomás confirma con un emoji y sigue con sus tareas del board. |
| Fin de semana | Se despliega el release con el formulario en su versión anterior. |
| Lunes, 9:20 hs | Ariadna detecta la caída de conversión en el dashboard. |
| Lunes, 10:00 hs | Se convoca la reunión de post-mortem. Participo como facilitador. |

## Análisis de causas

Identifico dos causas que actuaron en conjunto, no una sola.

**Causa de proceso:** el equipo no contaba con una norma que estableciera qué canal usar para pedidos de cambio de UI antes de un release, ni qué información mínima debía incluir ese pedido. El material del curso propone una plantilla mínima de comunicación asincrónica (título, resumen, contexto, acción requerida, plazo) que en este caso no se utilizó.

**Causa de priorización:** al no estar reflejado en el board del sprint, el pedido perdió visibilidad frente a las tareas que sí tenían seguimiento formal, y quedó fuera del radar de Tomás pese a la respuesta afirmativa que había dado.

Considero relevante aclarar que ninguna de las dos causas se explica por el desempeño individual de Tomás. Actuó de forma razonable frente a la información disponible; el punto débil está en la ausencia de un protocolo compartido, siguiendo el enfoque de post-mortem sin culpas que promueve la cultura de post-mortem constructiva.

## Acciones correctivas

- Se definió una plantilla obligatoria de mensaje asincrónico para cualquier pedido de cambio de UI previo a un release, con los campos título, resumen, contexto, acción requerida y plazo.
- Se acordó que ningún cambio de alcance se considera válido si no queda reflejado en el board del sprint, sin importar el canal por el que se haya conversado inicialmente.
- Se sumó un paso de verificación previo a cada release: cotejar el board contra los pedidos de cambio comunicados esa semana.

# Aprendizajes

El aprendizaje central de este caso es que la comunicación asincrónica efectiva no depende únicamente de la buena intención de quien pide un cambio, sino de que exista una estructura mínima compartida por todo el equipo. Un pedido informal, por más claro que le resulte a quien lo envía, no sustituye la trazabilidad de un ticket cuando hay varias personas y tareas en simultáneo.

También queda claro que un post-mortem bien conducido no busca identificar a quién señalar, sino qué parte del sistema de trabajo falló. Enfocar el análisis en el proceso, y no en las personas, fue lo que permitió que Martín y Tomás salieran de la reunión con una acción concreta en vez de con un conflicto sin resolver.

# Evidencia de control de versiones

Los cambios documentados en este post quedaron registrados en el repositorio público del ejercicio: [entrega_final--Ment_Crecim](https://github.com/JAMontagna/entrega_final--Ment_Crecim).

- Commit con el contenido completo del post: [`0b24f96` — Create index.md](https://github.com/JAMontagna/entrega_final--Ment_Crecim/commit/0b24f96)
- Commit con la plantilla de mensaje asincrónico, documentada como acción correctiva: [`d7cc78f` — Create plantilla-mensaje-asincronico.md](https://github.com/JAMontagna/entrega_final--Ment_Crecim/commit/d7cc78f)

# Reflexión sobre feedback radicalmente sincero

Durante la reunión del lunes, en mi rol de facilitador, observé que la primera devolución de Martín hacia Tomás estuvo centrada en el resultado ("no se hizo el cambio") más que en el comportamiento específico y observable que lo había generado. Señalé esta diferencia en el momento: el modelo de feedback radicalmente sincero (Radical Candor) exige describir el comportamiento concreto antes que el impacto, precisamente para que la conversación no se perciba como un reclamo personal.

A partir de esa intervención, Martín reformuló su devolución: reconoció que el pedido no había quedado en un canal trazable ni con un plazo explícito, y que esa era su responsabilidad como líder. Ese cambio de enfoque permitió que Tomás recibiera el intercambio sin actitud defensiva, y que la conversación derivara en una acción correctiva compartida en lugar de en una atribución de culpa unilateral.

Reconozco en este caso un ejemplo claro de por qué la seguridad psicológica y el feedback específico van de la mano: sin ese primer señalamiento sobre el enfoque de la devolución, es probable que la reunión hubiera reforzado la idea de que reportar errores tiene un costo personal, en lugar de fortalecer la disposición del equipo a hacerlo.
