---
title: Estatísticas do Projeto
menu:
    main:
        parent: Guia do Usuário
---

Cada projeto tem uma seção de estatísticas. Dependendo de como você está
usando Kanboard, você pode ver esses relatórios:

Repartição de usuário
=====================

![repartição do usuário](/images/v1/user-repartition.png)

Este gráfico de pizza mostra o número de tarefas abertas atribuídas por
usuário.

Distribuição de Tarefas
=======================

![distribuição de tarefas](/images/v1/task-distribution.png)

Este gráfico de pizza fornece uma visão geral do número de tarefas
abertas por coluna.

Diagrama de Fluxo Cumulativo
============================

![diagrama de fluxo cumulativo](/images/v1/cfd.png)

-   Este gráfico mostra o número de tarefas cumulativamente para cada
    coluna ao longo do tempo.
-   A ordem das legendas é a mesma que a pilha no gráfico.
-   A cor de cada coluna é determinada automaticamente.
-   Todos os dias, o número de tarefas é registrado para cada coluna.
-   Se você quiser excluir tarefas fechadas, altere as configurações
    globais do projeto.

Nota: Você precisa ter pelo menos dois dias de dados para ver o gráfico.

Gráfico de Burndown
===================

![gráfico Burndown](/images/v1/burndown-chart.png)

O [gráfico de burndown](http://en.wikipedia.org/wiki/Burn_down_chart)
está disponível para cada projeto.

-   Este gráfico é uma representação gráfica do trabalho a ser feito
    versus o tempo.
-   O Kanboard usa a complexidade ou o ponto da história para gerar esse
    diagrama.
-   Todos os dias, a soma dos pontos da história de cada coluna é
    calculada.

Tempo médio gasto em cada coluna
================================

![tempo médio gasto em cada coluna](/images/v1/average-time-spent-into-each-column.png)

Este gráfico mostra o tempo médio gasto em cada coluna para as últimas
1000 tarefas.

-   O Kanboard usa as transições de tarefas para calcular os dados.
-   O tempo gasto é calculado até que a tarefa seja encerrada.

Tempo médio de condução e ciclo
===============================

![tempo médio gasto em cada coluna](/images/v1/average-lead-cycle-time.png)

Este gráfico mostra o tempo médio de condução e de ciclo das últimas
1000 tarefas ao longo do tempo.

-   O tempo de condução é o tempo entre a criação da tarefa e a data da
    conclusão.
-   O tempo de ciclo é o tempo entre a data de início especificada da
    tarefa até a data de conclusão.
-   Se a tarefa não estiver fechada, a hora atual é usada em vez da data
    de conclusão.

Essas métricas são calculadas e registradas todos os dias para todo o
projeto.
