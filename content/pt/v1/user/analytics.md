---
title: Estatísticas do Projeto
menu:
    main:
        parent: Guia do Usuário
---

Cada projeto possui uma seção de estatísticas. Dependendo de como você utiliza o Kanboard, é possível visualizar os seguintes relatórios:

Repartição de Usuário
=====================

![repartição do usuário](/images/v1/user-repartition.png)

Este gráfico de pizza mostra o número de tarefas abertas atribuídas a cada usuário.

Distribuição de Tarefas
=======================

![distribuição de tarefas](/images/v1/task-distribution.png)

Este gráfico de pizza fornece uma visão geral do número de tarefas abertas em cada coluna.

Diagrama de Fluxo Cumulativo
============================

![diagrama de fluxo cumulativo](/images/v1/cfd.png)

-   Este gráfico exibe o número cumulativo de tarefas em cada coluna ao longo do tempo.
-   A ordem das legendas corresponde à ordem das pilhas no gráfico.
-   As cores de cada coluna são determinadas automaticamente.
-   Diariamente, o número de tarefas é registrado para cada coluna.
-   Para excluir tarefas fechadas, altere as configurações globais do projeto.

Nota: É necessário ter pelo menos dois dias de dados para visualizar este gráfico.

Gráfico de Burndown
===================

![gráfico Burndown](/images/v1/burndown-chart.png)

O [gráfico de burndown](http://en.wikipedia.org/wiki/Burn_down_chart) está disponível para cada projeto.

-   Este gráfico é uma representação visual do trabalho restante em relação ao tempo.
-   O Kanboard utiliza a complexidade ou os pontos da história para gerar este diagrama.
-   Diariamente, a soma dos pontos da história de cada coluna é calculada.

Tempo Médio Gasto em Cada Coluna
================================

![tempo médio gasto em cada coluna](/images/v1/average-time-spent-into-each-column.png)

Este gráfico mostra o tempo médio gasto em cada coluna para as últimas 1000 tarefas.

-   O Kanboard utiliza as transições de tarefas para calcular os dados.
-   O tempo gasto é calculado até que a tarefa seja concluída.

Tempo Médio de Condução e Ciclo
===============================

![tempo médio de condução e ciclo](/images/v1/average-lead-cycle-time.png)

Este gráfico mostra o tempo médio de condução e de ciclo das últimas 1000 tarefas ao longo do tempo.

-   O tempo de condução é o intervalo entre a criação da tarefa e a data de conclusão.
-   O tempo de ciclo é o intervalo entre a data de início especificada da tarefa e a data de conclusão.
-   Se a tarefa não estiver concluída, o horário atual será utilizado no lugar da data de conclusão.

Essas métricas são calculadas e registradas diariamente para todo o projeto.
