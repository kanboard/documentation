---
title: Configurações
menu:
    main:
        parent: Guia do Usuário
---

Alguns parâmetros do aplicativo podem ser alterados na página de
configurações. Somente administradores podem alterar essas
configurações.

Configurações do aplicativo
---------------------------

Vá até o menu **Configurações** e escolha **Configurações do
aplicativo** à esquerda.

![configurações do aplicativo](/images/v1/application-settings.png)

### URL do aplicativo

Este parâmetro é usado para notificações por e-mail. O rodapé do e-mail
conterá um link para a tarefa do Kanboard.

### Idioma

O idioma do aplicativo pode ser alterado a qualquer momento. O idioma
será definido para todos os usuários.

### Fuso horário

Por padrão, o Kanboard usa o UTC como fuso horário, mas você pode
definir o seu próprio fuso horário. A lista contém todos os fusos
horários aceitos pelo seu servidor web.

### Formato de data

Formato de entrada usado para campos de data, por exemplo, a data de
vencimento das tarefas.

O Kanboard oferece 4 formatos diferentes:

-   `DD/MM/AAAA`
-   `MM/DD/AAAA` (padrão)
-   `AAAA/MM/DD`
-   `MM.DD.AAAA`

O formato [ISO 8601](http://en.wikipedia.org/wiki/ISO_8601) é sempre
aceito (`AAAA-MM-DD` ou `AAAA_MM_DD`).

### Folha de estilo personalizada

Escreva seu próprio CSS para substituir ou melhorar o estilo padrão do
Kanboard.

Aqui está um exemplo para mudar a cor dos rótulos das categorias:

Para o contêiner da categoria:

```css
.task-board-category-container-color span {
  border: solid 0.5px grey;
  color: black;
}
```

Valores CSS personalizados para uma categoria - este é um exemplo para
exibir o texto:

```css
[class*="category-MyLabel"] {
  background-color: rgba(255, 0, 0, 0.50);
  border: none!important;
  font-weight: bold;
  font-style: italic;
  box-shadow: 0 1px 1px rgba(186, 186, 186, 0.55);
  color: white!important;
  font-size: 11px;
}
```

Configurações do projeto
------------------------

Vá até o menu **Configurações** e escolha **Configurações do projeto** à
esquerda.

![configurações do projeto](/images/v1/project-settings.png)

### Colunas padrão para novos projetos

Você pode alterar os nomes das colunas padrão aqui. É útil se você
sempre cria projetos com as mesmas colunas.

Cada nome de coluna deve ser separado por uma vírgula.

Por padrão, o Kanboard usa esses nomes de coluna: Backlog, A fazer, Em
andamento e Feito.

### Categorias padrão para novos projetos

As categorias não são globais para o aplicativo, mas estão anexadas a um
projeto. Cada projeto pode ter categorias diferentes.

No entanto, se você sempre cria as mesmas categorias para todos os seus
projetos, pode definir aqui a lista de categorias para criar
automaticamente.

### Permitir apenas uma subtarefa em andamento ao mesmo tempo para um usuário

Quando esta opção está habilitada, um usuário pode trabalhar com apenas
uma subtarefa por vez.

Se outra subtarefa tiver o status "em andamento", o usuário verá a
caixa de diálogo:

![restrição do usuário de subtarefa](/images/v1/subtask-user-restriction.png)

### Acionar o rastreamento de tempo de subtarefa automaticamente

-   Se ativado, quando o status de uma subtarefa for alterado para "em
    andamento", o temporizador será iniciado automaticamente.
-   Desative esta opção se você não usar o rastreamento de tempo.

### Incluir tarefas fechadas no diagrama de fluxo cumulativo

-   Se habilitado, as tarefas fechadas serão incluídas no diagrama de fluxo cumulativo.
-   Se desativado, apenas as tarefas abertas serão incluídas.
-   Esta opção afeta a coluna `total` da tabela `project_daily_column_stats`.

Configurações do quadro
-----------------------

Vá até o menu **Configurações** e escolha **Configurações do painel** à
esquerda.

![configurações da placa](/images/v1/board-settings.png)

### Destaque da Tarefa

Esse recurso exibe uma sombra ao redor da tarefa quando uma tarefa foi
movida recentemente.

Defina o valor 0 para desativar esse recurso. O padrão é 2 dias (172800
segundos).

Tudo que mudou nos últimos 2 dias terá uma sombra ao redor da tarefa.

### Intervalo de atualização para quadro público

Quando você compartilha um quadro, a página será atualizada a cada 60
segundos automaticamente por padrão.

### Intervalo de atualização para o quadro privado

Quando o seu navegador está aberto em um quadro, o Kanboard verifica a
cada 10 segundos se algo foi alterado por outra pessoa.

Tecnicamente, esse processo é feito por polling Ajax.

Configurações do calendário
---------------------------

Vá até o menu **Configurações** e escolha **Configurações de
calendário** à esquerda.

![configurações do calendário](/images/v1/calendar-settings.png)

Existem dois calendários diferentes no Kanboard:

-   Calendário do projeto
-   Calendário do usuário (disponível no painel)

### Calendário do Projeto

Este calendário mostra tarefas com data de vencimento definida e tarefas
baseadas na data de criação ou na data de início.

Mostrar tarefas com base na data de criação:

-   A data de início do evento de calendário é a data de criação da
    tarefa.
-   A data final do evento é a data de conclusão.

Mostrar tarefas com base na data de início:

-   A data de início do evento do calendário é a data de início da
    tarefa.
-   Esta data pode ser definida manualmente.
-   A data final do evento é a data de conclusão.
-   Se não houver data de início, a tarefa não aparecerá no calendário.

### Calendário do usuário

Este calendário mostra apenas as tarefas atribuídas ao usuário e,
opcionalmente, informações de subtarefas.

Mostrar subtarefas com base no rastreamento de tempo:

-   Exibir subtarefas no calendário a partir das informações registradas
    na tabela de controle de tempo.
-   A interseção com o horário do usuário também é calculada.

Mostrar estimativas de subtarefa (previsão de trabalho futuro):

-   Exibir a estimativa do trabalho futuro para subtarefas no status
    "A fazer" e com um valor definido de "estimativa".

Configurações de Link
---------------------

As relações de tarefas podem ser alteradas a partir das configurações do
aplicativo (**Configurações > Configurações de link**).

![Link Labels](/images/v1/link-labels.png)

Cada etiqueta pode ter um rótulo oposto definido.
Se não houver oposto, o rótulo é considerado bidirecional.

![Link Label Creation](/images/v1/link-label-creation.png)
