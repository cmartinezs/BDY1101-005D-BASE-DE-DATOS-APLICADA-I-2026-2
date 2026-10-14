# Laboratorio guiado · Primer contacto con Oracle APEX

**BDY1101 · EA2 · Introducción al entorno, sin crear tablas SQL.**

## Objetivo y alcance

Reconocer el entorno APEX, identificar la diferencia entre instancia, workspace, aplicación y página, y construir una navegación básica. Es una actividad de exploración que prepara la experiencia posterior, pero **no requiere crear tablas ni ejecutar DDL/DML/consultas SQL**.

El taller institucional de semana 10 solicita: (1) acceso a instancia, (2) workspace y (3) páginas de inicio, reportes, gráficos y configuración. Su indicador IL 3.6 está asociado a dashboards mediante SQL; esa implementación se trabajará posteriormente. Esta adaptación separa la familiarización del desarrollo sobre datos reales.

## Requisitos

- Navegador actualizado y conexión a internet.
- Cuenta y acceso a un **workspace APEX** proporcionado por docente/institución o autorizado para prácticas.
- No contratar infraestructura ni introducir tarjetas de pago para completar la actividad.
- La nomenclatura de menús cambia según versión, idioma y modalidad de servicio.

## Paso 1 · Ingresar

1. Abrir la URL de APEX facilitada por el docente.
2. Introducir workspace, usuario y contraseña, según la pantalla.
3. Confirmar acceso al inicio del workspace.
4. Identificar **App Builder**, **SQL Workshop**, **Team Development** y utilidades del entorno. En esta actividad no es necesario usar SQL Workshop.
5. Guardar una captura del inicio sin mostrar contraseñas ni datos sensibles.

Si no se dispone de workspace, no inventar credenciales. Solicitar acceso a uno existente. La creación de una instancia de servicio en Oracle Cloud **no es lo mismo** que la solicitud de un workspace de desarrollo.

## Paso 2 · Reconocer la estructura

- **Instancia/servicio:** alojamiento y administración de APEX.
- **Workspace:** espacio lógico de trabajo con usuarios y aplicaciones.
- **Aplicación:** conjunto de páginas con navegación y configuración común.
- **Página:** pantalla concreta de una aplicación.
- **App Builder:** herramienta para diseñar las aplicaciones y páginas.

Antes de construir nada, ubicar el botón **Create / Crear** en App Builder.

## Paso 3 · Crear una aplicación vacía

1. Entrar a **App Builder → Create / Crear**.
2. Escoger **New Application / Nueva aplicación** (o equivalente).
3. Darle el nombre **Exploración APEX - BDY1101**.
4. Conservar las opciones por defecto que no sean requeridas expresamente.
5. Confirmar la creación y abrir el diseñador de aplicación.
6. Identificar el listado de páginas y la opción **Add Page / Crear página**.

No modificar opciones de seguridad avanzadas sin indicación institucional.

## Paso 4 · Revisar la página de inicio

1. Buscar la página de inicio generada por APEX.
2. Abrirla en Page Designer y reconocer las regiones: árbol de componentes, vista de diseño y editor de propiedades.
3. Usar la navegación existente o configurar accesos a las páginas que se crearán.
4. Guardar y ejecutar para comprobar que la aplicación abre.

## Paso 5 · Páginas de exploración

Crear páginas **Reportes**, **Gráficos** y **Configuración**, según los asistentes disponibles en la versión utilizada.

- **Reportes:** si APEX exige una fuente de datos para una página tipo reporte, no improvisar tablas ni SQL. Crear una página en blanco titulada “Reportes — próxima etapa” y documentar que el componente de reporte real quedará pendiente de EA3 o del dataset que entregue el docente.
- **Gráficos:** aplicar el mismo criterio; si el componente exige SQL/datos, crear una página informativa y reservar el gráfico real para EA3.
- **Configuración:** crear una página básica sin alterar parámetros de seguridad o del workspace.
- **Página de Duoc:** si la pauta la exige, crear un acceso informativo que remita al sitio institucional autorizado; no exponer información privada.

Los nombres exactos de las opciones y plantillas pueden variar entre versiones de APEX.

## Paso 6 · Verificar navegación

1. Ejecutar la aplicación.
2. Comprobar acceso desde Inicio a las páginas creadas.
3. Volver a Inicio usando la navegación.
4. Revisar títulos, ortografía y consistencia de nombres.
5. Guardar capturas del listado de páginas y de la aplicación en ejecución.

## Entrega sugerida

Captura de la pantalla del workspace, listado de páginas y breve explicación escrita de cada concepto: instancia, workspace, aplicación y página. No entregar credenciales ni datos personales.

## Problemas frecuentes

- **No puedo entrar:** revisar URL, workspace y usuario; si es cuenta institucional, consultar acceso.
- **No encuentro una opción:** verificar idioma y versión; buscar en App Builder/Page Designer.
- **Reportes o gráficos piden datos:** es esperado; detenerse y usar una página placeholder, sin saltar a SQL.
- **No abre mi aplicación:** confirmar que se haya guardado y usar Run / Ejecutar desde App Builder.

Referencia institucional de instancia Oracle Cloud: https://docs.oracle.com/es-ww/iaas/apex/doc/create-and-set-up-apex-service-instance.html

> Este documento es una **adaptación pedagógica EA2**, no una sustitución del taller oficial ni una afirmación de que el indicador IL 3.6 se encuentra cumplido.
