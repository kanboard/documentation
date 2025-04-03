---
title: Rastreamento de tempo
menu:
    main:
        parent: Guia do Usuário
---

As informações de rastreamento de tempo podem ser definidas no nível da
tarefa ou no nível de subtarefa.

Rastreamento de tempo da tarefa
-------------------------------

![rastreamento do tempo da tarefa](/images/v1/task-time-tracking.png)

Tarefas possuem dois campos:

-   Tempo estimado
-   Tempo gasto

Esses valores representam horas de trabalho e precisam ser definidos
manualmente.

Acompanhamento de tempo de subtarefa
------------------------------------

![rastreamento de tempo de subtarefa](/images/v1/subtask-time-tracking.png)

As subtarefas também têm os campos "tempo gasto" e "tempo estimado".

Quando você altera o valor desses campos, **o rastreamento do tempo da
tarefa e os valores são atualizados automaticamente e se tornam a soma de
todas as subtarefas e valores**.

Kanboard registra o tempo entre cada mudança de status de subtarefa em
uma tabela separada.

-   Alterar o status da subtarefa de **A fazer** para **em progresso**
    registra a hora de início
-   Alterar o status da subtarefa de **em progresso** para **concluído**
    registra o tempo final, mas também atualiza o tempo gasto da
    subtarefa e da tarefa

A divisão de todos os registros é visível na página de visualização de
tarefas:

![quadro de horários da tarefa](/images/v1/task-timesheet.png)

Para cada subtarefa, o cronômetro pode ser interrompido/iniciado a
qualquer momento:

![temporizador de subtarefa](/images/v1/subtask-timer.png)

-   O cronômetro não depende do status da subtarefa
-   Cada vez que você inicia o temporizador, um novo registro é criado
    na tabela de rastreamento de tempo
-   Cada vez que você para o relógio, a data final é gravada na tabela
    de rastreamento de tempo
-   O tempo gasto é arredondado para o trimestre mais próximo (somente
    para Kanboard < 1.0.32)
