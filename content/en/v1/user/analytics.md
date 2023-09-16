---
title: Project Analytics
toc: true
menu:
    main:
        parent: Using Kanboard
---

Each project has an analytics section. Depending on how you are using Kanboard, you can see those reports:

User Repartition
----------------

![User Repartition](/images/v1/user-repartition.png)

This pie chart show the number of open tasks assigned per user.

Task Distribution
-----------------

![Task Distribution](/images/v1/task-distribution.png)

This pie chart gives an overview of the number of open tasks per column.

Cumulative Flow Diagram
-----------------------

![Cumulative Flow Diagram](/images/v1/cfd.png)

- This chart shows the number of tasks cumulatively for each column over the time.
- The legend order is the same as the stack in the chart.
- The color of each column is determined automatically.
- Every day, the number of tasks is recorded for each column.
- If you would like to exclude closed tasks, change the global project settings.

Note: You need to have at least two days of data to see the graph.

Burn Down Chart
---------------

![Burn Down Chart](/images/v1/burndown-chart.png)

The [burn down chart](http://en.wikipedia.org/wiki/Burn_down_chart) is
available for each project.

- This chart is a graphical representation of work left to do versus time.
- Kanboard use the complexity or story point to generate this diagram.
- Everyday, the sum of the story points for each column is calculated.

Average Time Spent Into Each Column
-----------------------------------

![Average Time Spent Into Each Column](/images/v1/average-time-spent-into-each-column.png)

This chart shows the average time spent into each column for the last 1000 tasks.

- Kanboard uses the task transitions to calculate the data.
- The time spent is calculated until the task is closed.

Average Lead and Cycle time
---------------------------

![Average Lead and Cycle time](/images/v1/average-lead-cycle-time.png)

This chart show the average lead and cycle time for the last 1000 tasks
over time.

- The lead time is the time between the task creation and the date of completion.
- The cycle time is time between the specified start date of the task to the completion date.
- If the task is not closed, the current time is used instead of the date of completion.

Those metrics are calculated and recorded every day for the whole project.
