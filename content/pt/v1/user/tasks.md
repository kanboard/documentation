---
title: Tarefas
menu:
    main:
        parent: Guia do Usuário
---

Criando Tarefas
---------------

No quadro, clique no sinal de mais ao lado do nome da coluna:

![criação de tarefas a partir do quadro](/images/v1/task-creation-board.png)

Em seguida, o formulário de criação de tarefas será exibido:

![formulário de criação de tarefas](/images/v1/task-creation-form.png)

-   **Título**: O título da sua tarefa, que será exibido no quadro.
-   **Descrição**: Descrição que usa a sintaxe do Markdown.
-   **Etiquetas**: Lista de etiquetas associadas à tarefa.
-   **Criar outra tarefa**: Marque esta caixa se você quiser criar uma
    tarefa semelhante (alguns campos serão pré-preenchidos).
-   **Cor**: Escolha a cor do cartão.
-   **Responsável**: A pessoa que irá trabalhar na tarefa.
-   **Categoria**: Apenas uma categoria pode ser atribuída a uma tarefa
    (visível somente se os projetos tiverem categorias).
-   **Coluna**: A coluna onde a tarefa será criada. Sua tarefa será
    posicionada na parte inferior.
-   **Prioridade**: Prioridade da tarefa. O intervalo pode ser definido
    nas configurações do projeto. Os valores padrão são P0 a P3.
-   **Complexidade**: Utilizado no gerenciamento ágil de projetos
    (Scrum). A complexidade ou pontos de história é um número que indica
    à equipe o quão difícil a história é. Muitas vezes, as pessoas usam
    a série de Fibonacci.
-   **Referência**: ID externo para a tarefa, por exemplo, pode ser o
    número do bilhete que vem de outro sistema.
-   **Estimativa original**: Estimativa em horas para concluir a tarefa.
-   **Tempo Gasto**: Tempo gasto trabalhando na tarefa.
-   **Data de início**: Este é um campo de data e hora.
-   **Data de Vencimento**: As tarefas vencidas terão uma data de
    vencimento em vermelho, enquanto as datas que ainda não venceram
    estarão em preto no quadro. Vários formatos de data são aceitos
    além do selecionador de data.

Com o link de visualização, você pode ver a descrição da tarefa
convertida da sintaxe do Markdown.

Duplicando e Movendo Tarefas
----------------------------

### Duplicar uma tarefa no mesmo projeto

Vá para a visualização de tarefas e escolha **Duplicar** à esquerda.

![duplicação de tarefas](/images/v1/task-duplication.png)

Uma nova tarefa será criada com as mesmas propriedades do original.

### Duplicar uma tarefa para outro projeto

Vá para a visualização da tarefa e escolha **Duplicar para outro projeto**.

![Duplicação de Tarefas Outro Projeto](/images/v1/task-duplication-another-project.png)

Somente projetos nos quais você é membro serão exibidos na lista
suspensa.

Antes de copiar as tarefas, o Kanboard perguntará as propriedades
destino que não são comuns entre o projeto de origem e o projeto de destino.

Basicamente, você precisa definir:

-   A raia de destino
-   A coluna
-   A categoria
-   O responsável

### Mover uma tarefa para outro projeto

Vá para a visualização de tarefas e escolha **Mover para outro
projeto**.

Mover uma tarefa para outro projeto funciona da mesma maneira que a
duplicação. Você terá que escolher as novas propriedades da tarefa.

### Lista de propriedades duplicadas

-   `title`
-   `description`
-   `date_due`
-   `color_id`
-   `project_id`
-   `column_id`
-   `owner_id`
-   `score`
-   `category_id`
-   `time_estimated`
-   `swimlane_id`
-   `recurrence_status`
-   `recurrence_trigger`
-   `recurrence_factor`
-   `recurrence_timeframe`
-   `recurrence_basedate`

Fechando Tarefas
----------------

Quando uma tarefa é fechada, ela fica oculta do quadro.

No entanto, você sempre pode acessar a lista de tarefas fechadas usando
a consulta **status:closed** em qualquer formulário de pesquisa ou
simplesmente selecionando **Tarefas fechadas** no menu suspenso do
filtro.

Existem duas maneiras diferentes de fechar uma tarefa, pelo menu suspenso
de tarefas no quadro:

![fecha uma tarefa no menu suspenso](/images/v1/menu-close-task.png)

Ou no menu da barra lateral da tarefa, na visualização dos detalhes da
tarefa:

![fechar tarefa](/images/v1/closing-tasks.png)

Nota: Quando você fechar uma tarefa, todas as subtarefas não concluídas
serão alteradas para o status **Finalizada**.

Links de tarefas internas
-------------------------

As tarefas podem ser vinculadas a relacionamentos pré-definidos:

![Links de tarefas](/images/v1/internal-task-links.png)

Também é possível vincular tarefas entre projetos.

Os relacionamentos padrão são:

-   **refere-se à**
-   **bloqueia** | **está bloqueada por**
-   **duplicadas** | **é duplicada por**
-   **é filha de** | **é pai de**
-   **alvos marco** | **é um marco de**
-   **corrige** | **é corrigido por**

Esses rótulos podem ser alterados nas configurações do aplicativo.

Transições de tarefas
---------------------

Cada movimento de uma tarefa entre colunas é registrado no banco de
dados.

![Transições de tarefa](/images/v1/task-transitions.png)

Disponível na visualização de tarefas, você pode ver essas informações:

-   Data da ação
-   Coluna de origem
-   Coluna de destino
-   Executor (usuário que moveu a tarefa)
-   Tempo gasto na coluna de origem

Tarefas recorrentes
-------------------

Para se encaixar na metodologia Kanban, as tarefas recorrentes não são
baseadas em uma data, mas em eventos do quadro.

-   As tarefas recorrentes são duplicadas para a primeira coluna do
    quadro quando os eventos selecionados ocorrem.
-   A data de vencimento pode ser recalculada automaticamente.
-   Cada tarefa registra o ID da tarefa pai que a criou e a tarefa filha
    criada.

### Configuração

Vá para a página de visualização de tarefas ou use o menu suspenso no
quadro; selecione **Editar recorrência**.

![tarefa recorrente](/images/v1/recurring-tasks.png)

Existem três gatilhos que atualmente criam uma nova tarefa recorrente:

-   Movendo uma tarefa da primeira coluna
-   Movendo uma tarefa para a última coluna
-   Fechando a tarefa

As datas de vencimento, se definidas na tarefa atual, podem ser
recalculadas por um dado fator de dias, meses ou anos. A data base para
o cálculo da nova data de vencimento pode ser a data de vencimento
existente ou a data da ação.

Adicionando Capturas de Tela
----------------------------

Você pode copiar e colar imagens diretamente no Kanboard para economizar
tempo. Estas imagens são carregadas como anexos da tarefa.

Isso é especialmente útil para fazer capturas de tela para descrever um
problema, por exemplo.

Você pode adicionar capturas de tela diretamente do quadro clicando no
menu suspenso ou na página de visualização de tarefas.

![menu de captura de tela suspensa](/images/v1/dropdown-screenshot.png)

Para adicionar uma nova imagem, faça sua captura de tela e cole com
CTRL+V ou Comando+V:

![Página de captura de tela](/images/v1/task-screenshot.png)

No macOS, você pode usar esses atalhos para fazer capturas de tela:

-   Command-Control-Shift-3: Faça uma captura de tela da tela e salve-a
    na área de transferência.
-   Command-Control-Shift-4, em seguida, selecione uma área: Faça uma
    captura de tela da área e salve-a na área de transferência.
-   Command-Control-Shift-4, depois espaço, depois clique em uma janela:
    Captura de tela de uma janela e salve-a na área de transferência.

Existem também vários aplicativos de terceiros que podem ser usados
para capturas de tela com anotações e formas.

Etiquetas
---------

Com o Kanboard, você pode associar uma ou mais etiquetas a uma tarefa.
Você pode definir etiquetas globalmente para todos os projetos ou apenas
para um projeto específico.

![Etiquetas no quadro](/images/v1/tags-board.png)

No formulário da tarefa, você pode inserir as etiquetas desejadas:

![formulário de etiquetas](/images/v1/tags-task.png)

O formulário de preenchimento automático será exibido para sugerir as
etiquetas disponíveis.

Você também pode criar etiquetas diretamente no formulário de tarefas.
Por padrão, quando você cria etiquetas em um formulário de tarefas,
elas são associadas ao projeto atual:

![Etiquetas do projeto](/images/v1/tags-projects.png)

Todas as etiquetas podem ser gerenciadas nas configurações do projeto.

Para definir etiquetas globalmente para todos os projetos, vá para as
configurações do aplicativo:

![Etiquetas globais](/images/v1/tags-global.png)

Para pesquisar tarefas com base em etiquetas, basta usar o atributo
"etiqueta":

![Pesquisar Etiquetas](/images/v1/tags-search.png)

Estatísticas
------------

Cada tarefa tem uma seção de estatísticas disponível no menu à esquerda
na exibição de tarefa.

### Tempo de Execução e Tempo de Ciclo

![lead e tempo de ciclo](/images/v1/task-lead-cycle-time.png)

-   O tempo de execução é o tempo entre a criação da tarefa e a data da
    conclusão (tarefa fechada).
-   O tempo de ciclo é o tempo entre a data de início e a data
    de conclusão.
-   Se a tarefa não for fechada, a hora atual é usada em vez da data de
    conclusão.
-   Se a data de início não for especificada, o tempo do ciclo não será
    calculado.

Nota: Você pode configurar uma ação automática para definir a data de
início automaticamente quando você move uma tarefa para a coluna de sua
escolha.

### Tempo gasto em cada coluna

![tempo gasto em cada coluna](/images/v1/time-into-each-column.png)

-   Este gráfico mostra o tempo total gasto em cada coluna para a
    tarefa.
-   O tempo gasto é calculado até que a tarefa seja encerrada.
