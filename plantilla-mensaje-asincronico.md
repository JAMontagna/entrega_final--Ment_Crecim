# Plantilla de mensaje asincrónico para cambios de UI pre-release

Este archivo documenta la acción correctiva definida en la reunión de post-mortem del caso Nimbus (ver `index.md`). A partir de este incidente, cualquier pedido de cambio de UI antes de un release debe comunicarse usando esta estructura, sin importar el canal (Slack, email, comentario en el board).

## Campos obligatorios

**Título:** resumen de una línea del cambio solicitado.

**Resumen:** qué se pide, en una o dos oraciones.

**Contexto:** por qué se pide el cambio (hallazgo de un test, reporte de un bug, feedback de un usuario, etc.).

**Acción requerida:** qué tiene que hacer específicamente la persona que recibe el pedido.

**Plazo:** fecha u horario límite. Si no hay plazo estricto, se aclara explícitamente "sin plazo fijo, no bloquea el release en curso".

## Regla complementaria

Ningún pedido de cambio de UI se considera válido para un release si no está reflejado también como tarjeta en el board del sprint, independientemente del canal por el que se haya comunicado inicialmente.

## Ejemplo aplicado al caso Nimbus

Así debería haberse comunicado el pedido que originó el incidente:

**Título:** Simplificar formulario de onboarding antes del release del lunes.

**Resumen:** Sacar dos campos opcionales del formulario de onboarding y mover un tercero a un paso posterior del flujo.

**Contexto:** El test de usabilidad de esta semana mostró abandono antes de que el usuario percibiera valor, por exceso de campos en el primer paso.

**Acción requerida:** Actualizar el formulario según el nuevo flujo adjunto y crear la tarjeta correspondiente en el board del sprint antes del viernes a las 18 hs.

**Plazo:** Viernes 18 hs. Si no se llega, el cambio queda para el siguiente release, no se prioriza sobre otras tareas ya asignadas.
