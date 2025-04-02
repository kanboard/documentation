---
title: Análisis
menu:
    main:
        parent: Guía del usuario
---

Cada proyecto tiene una sección de análisis. Dependiendo de cómo se está utilizando Kanboard, se puede ver estos informes:

Repartición de usuarios
-----------------------

![User repartition](/images/v1/user-repartition.png)

Este gráfico de sectores muestra el número de tareas abiertas asignadas por usuario.

Distribución de tareas
----------------------

![Task distribution](/images/v1/task-distribution.png)

Este gráfico de sectores da una visión general del número de tareas abiertas por columnas.

Diagrama de flujo acumulado
---------------------------

![Cumulative flow diagram](/images/v1/cfd.png)

- Este gráfico muestra el número de tareas acumuladas por cada columna a través del tiempo.
- Cada día, el número total de tareas se registra para cada columna.
- Si tú quisieras excluir las tareas cerradas, deberás cambiar las configuraciones globales del proyecto.

Nota: Necesitas tener al menos dos días de datos para ver la gráfica.


Gráfico Burn down
----------------

El gráfico burn down está disponible para cada proyecto.

- Este gráfico es una representación gráfica del trabajo laborado contra el tiempo.
- Kanboard usa la complejidad o historia de puntos para generar este diagrama.
- Todos los días, se calcula la suma de los puntos de la historia de cada columna.

Tiempo promedio en cada columna
-----------------------------

Este gráfico muestra el tiempo promedio dedicado en cada columna para las últimas 1000 tareas.

- Kanboard usa las transiciones de tareas para calcular los datos.
- El tiempo dedicado se calcula hasta que la tarea se cierra.


Promedio de avances y ciclos de tiempos
-------------------------------------

Este gráfico muestra el promedio de avances y ciclo de tiempos para las últimas 1000 tareas fuera de tiempo.

- El tiempo promedio es el tiempo entre la creación de la tarea y la fecha de finalización.
- El tiempo de ciclo se encuentra entre la fecha de inicio de la tarea especificada y fecha de la tarea finalizada.
- Si la tarea no está cerrada, el momento actual se utiliza en lugar de la fecha de finalización.

Esos indicadores se calculan y registran todos los días durante todo el proyecto.

Nota: No olvidar ejecutar todos los días el cronjob para tener estadísticas precisas.
