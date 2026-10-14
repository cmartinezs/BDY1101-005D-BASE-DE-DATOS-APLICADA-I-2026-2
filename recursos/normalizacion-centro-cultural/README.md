# Normalización paso a paso · Centro Cultural «La Estación»

**BDY1101 · EA2 / EV2 · Caso docente de repaso, sin SQL.**

[**Abrir presentación interactiva HTML (20 diapositivas)**](./normalizacion_slides_EV2.html)

## Objetivo

A partir de una ficha de inscripciones, reconocer grupos repetitivos, dependencias parciales y dependencias transitivas. Explicar cómo cambia el modelo desde una estructura inicial hasta tercera forma normal, y justificar las claves y relaciones.

## Reglas del caso

- Un estudiante tiene un identificador único.
- Un taller tiene un identificador único, nombre y una sala asignada.
- Cada sala tiene código y nombre propios.
- En el modelo simplificado cada estudiante se inscribe como máximo una vez por taller.
- La fecha de inscripción corresponde al vínculo concreto estudiante–taller.

## Estado inicial: vista de usuario sin normalizar

| ID estudiante | Nombre | Talleres inscritos | Salas |
| --- | --- | --- | --- |
| E01 | Ana Rojas | T10 Dibujo; T20 Guitarra | S1 Arte; S2 Música |
| E02 | Leo Soto | T10 Dibujo | S1 Arte |

**¿Qué falla?** Talleres y salas aparecen como listas paralelas dentro de celdas. Para retirar solo una inscripción hay que editar texto y mantener sincronizadas las listas. También cuesta contar participantes de un taller y controlar cambios de sala.

## 1FN · Una inscripción por fila

| id_estudiante | nombre | id_taller | nombre_taller | id_sala | nombre_sala | fecha |
| --- | --- | --- | --- | --- | --- | --- |
| E01 | Ana Rojas | T10 | Dibujo | S1 | Arte | 04/10 |
| E01 | Ana Rojas | T20 | Guitarra | S2 | Música | 05/10 |
| E02 | Leo Soto | T10 | Dibujo | S1 | Arte | 06/10 |

Cada celda ahora contiene un solo valor y cada fila un hecho de inscripción. Para este dominio simplificado, la pareja **(id_estudiante, id_taller)** identifica la inscripción. 1FN no elimina toda redundancia: Ana sigue repetida entre filas y Dibujo aparece por cada participante.

## 2FN · Eliminar dependencias parciales

Dependencias funcionales del caso:

- `id_estudiante → nombre_estudiante`
- `id_taller → nombre_taller, id_sala, nombre_sala`
- `(id_estudiante, id_taller) → fecha`

En una tabla de clave compuesta, el nombre del estudiante depende solo de una parte de la clave; lo mismo ocurre con los datos del taller. Por eso se distinguen:

- **ESTUDIANTE** (id_estudiante **PK**, nombre)
- **TALLER** (id_taller **PK**, nombre_taller, id_sala, nombre_sala)
- **INSCRIPCION** (id_estudiante **PK/FK**, id_taller **PK/FK**, fecha)

Las dos columnas de INSCRIPCION constituyen juntas la clave primaria compuesta; ambas referencian a sus entidades de origen. Ahora se puede cambiar el nombre de Ana sin editar todas sus inscripciones.

## 3FN · Eliminar dependencia transitiva

En TALLER aún existe `id_taller → id_sala → nombre_sala`. El nombre de la sala depende de la identidad de la sala, no del taller en sí. Por tanto, el modelo final es:

- **ESTUDIANTE** (id_estudiante **PK**, nombre)
- **SALA** (id_sala **PK**, nombre_sala)
- **TALLER** (id_taller **PK**, nombre_taller, id_sala **FK**)
- **INSCRIPCION** (id_estudiante **PK/FK**, id_taller **PK/FK**, fecha)

Relaciones: SALA 1:N TALLER; ESTUDIANTE 1:N INSCRIPCION; TALLER 1:N INSCRIPCION. La relación ESTUDIANTE N:M TALLER se resuelve mediante INSCRIPCION.

## Anomalías que desaparecen

- **Actualización:** renombrar la sala S1 se hace en SALA, una sola vez.
- **Inserción:** se puede registrar un taller incluso sin inscripciones.
- **Eliminación:** borrar la última inscripción no elimina los datos del taller.

## Preguntas para discusión

1. Si Ana deja Guitarra, ¿qué debería borrarse y qué debería conservarse?
2. ¿Por qué `id_estudiante` por sí solo no identifica una inscripción?
3. ¿Cuál atributo viola 2FN en la tabla de 1FN?
4. ¿Por qué `nombre_sala` debe vivir en SALA?
5. **Bonus:** si alguien cursa el mismo taller en 2026 y 2027, ¿sigue siendo suficiente la clave compuesta? No: habría que incorporar edición/período o definir identificador de inscripción y unicidad de negocio.

## Alcance

Este es un caso para **analizar y modelar**, no para crear tablas con SQL. La implementación física se reserva para EA3.
