---
title: Ações Automáticas
menu:
    main:
        parent: Guia do Usuário
---

Para minimizar a interação do usuário, o Kanboard suporta ações automatizadas.

Cada ação automática é definida com as seguintes propriedades:

-   Um evento para ouvir
-   Ação vinculada ao evento
-   Parâmetros adicionais

Cada projeto tem um conjunto diferente de ações automáticas. O painel de configuração está localizado na página de listagem do projeto - basta clicar no link **Ações automáticas**.

Adicione uma nova ação
----------------------

Clique no link **Adicionar uma nova ação automática**.

![Ação Automática](/images/v1/automatic-action-creation.png)

1.  Escolha uma ação.
2.  Selecione um evento.
3.  Defina os parâmetros.

Ações disponíveis
-----------------

-   Criar um comentário de um provedor externo.
-   Adicionar um log de comentários ao mover a tarefa entre colunas.
-   Atribuir automaticamente uma categoria com base em uma cor.
-   Alterar a categoria com base em um rótulo externo.
-   Atribuir automaticamente uma categoria com base em um link.
-   Atribuir automaticamente uma cor com base em uma categoria.
-   Atribuir uma cor quando a tarefa é movida para uma coluna específica.
-   Alterar a cor da tarefa ao usar um link de tarefa específico.
-   Atribuir uma cor a um usuário específico.
-   Atribuir a tarefa à pessoa que realiza a ação.
-   Atribuir a tarefa à pessoa que realiza a ação quando a coluna é modificada.
-   Atribuir a tarefa a um usuário específico.
-   Alterar o responsável com base em um nome de usuário externo.
-   Fechar a tarefa.
-   Fechar uma tarefa em uma coluna específica.
-   Criar uma tarefa de um provedor externo.
-   Duplicar a tarefa para outro projeto.
-   Enviar uma tarefa por e-mail para alguém.
-   Mover a tarefa para outro projeto.
-   Mover a tarefa para outra coluna quando atribuída a um usuário.
-   Mover a tarefa para outra coluna quando a categoria for alterada.
-   Mover a tarefa para outra coluna quando o responsável for removido.
-   Abrir uma tarefa.
-   Atualizar automaticamente a data de início.

Exemplos
--------

Aqui estão alguns exemplos usados na prática:

### Quando movo uma tarefa para a coluna "Concluído", fecho esta tarefa automaticamente

-   Escolha uma ação: **Fechar uma tarefa em uma coluna específica**.
-   Escolha o evento: **Mover uma tarefa para outra coluna**.
-   Defina o parâmetro de ação: **Coluna = Concluído** (esta é a coluna de destino).

### Quando movo uma tarefa para a coluna "Para ser validado", atribuo essa tarefa a um usuário específico

-   Escolha a ação: **Atribuir a tarefa a um usuário específico**.
-   Escolha o evento: **Mover uma tarefa para outra coluna**.
-   Defina os parâmetros de ação: **Coluna = Para ser validado** e **Usuário = Bob** (Bob é nosso testador).

### Quando movo uma tarefa para a coluna "Trabalho em andamento", atribuo essa tarefa ao usuário atual

-   Escolha a ação: **Atribuir a tarefa à pessoa que realiza a ação quando a coluna é alterada**.
-   Escolha o evento: **Mover uma tarefa para outra coluna**.
-   Defina o parâmetro de ação: **Coluna = Trabalho em andamento**.

### Quando uma tarefa é concluída, duplico essa tarefa para outro projeto

Digamos que temos dois projetos: "Pedidos do cliente" e "Produção". Uma vez que o pedido é validado, mova-o para o projeto "Produção".

-   Escolha uma ação: **Duplicar a tarefa para outro projeto**.
-   Escolha o evento: **Fechar uma tarefa**.
-   Defina os parâmetros de ação: **Coluna = Validado** e **Projeto = Produção**.

### Quando uma tarefa é movida para a última coluna, movo exatamente a mesma tarefa para outro projeto

Digamos que temos dois projetos: "Ideias" e "Desenvolvimento". Uma vez que a ideia é validada, mova-a para o projeto "Desenvolvimento".

-   Escolha uma ação: **Mover a tarefa para outro projeto**.
-   Escolha o evento: **Mover uma tarefa para outra coluna**.
-   Defina os parâmetros de ação: **Coluna = Validado** e **Projeto = Desenvolvimento**.

### Quero atribuir automaticamente uma cor ao usuário Bob

-   Escolha uma ação: **Atribuir uma cor a um usuário específico**.
-   Escolha o evento: **Alteração do responsável da tarefa**.
-   Defina os parâmetros de ação: **Cor = Verde** e **Usuário = Bob**.

### Quero atribuir uma cor automaticamente à categoria definida como "Solicitação de recurso"

-   Escolha uma ação: **Atribuir automaticamente uma cor com base em uma categoria**.
-   Escolha o evento: **Criação ou modificação de tarefas**.
-   Defina os parâmetros de ação: **Cor = Azul** e **Categoria = Solicitação de recurso**.

### Desejo definir a data de início automaticamente quando a tarefa for movida para a coluna "Trabalho em andamento"

-   Escolha uma ação: **Atualizar automaticamente a data de início**.
-   Escolha o evento: **Mover uma tarefa para outra coluna**.
-   Defina o parâmetro de ação: **Coluna = Trabalho em andamento**.
