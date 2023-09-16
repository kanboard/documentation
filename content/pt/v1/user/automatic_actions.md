---
title: Ações Automáticas
menu:
    main:
        parent: Guia do Usuário
---

Para minimizar a interação do usuário, o Kanboard suporta ações
automatizadas.

Cada ação automática é definida com estas propriedades:

-   Um evento para ouvir
-   Ação ligada ao evento
-   Parâmetros adicionais

Cada projeto tem um conjunto diferente de ações automáticas. O painel de
configuração está localizado na página de listagem do projeto - basta
clicar no link **Ações automáticas**.

Adicione uma nova ação
----------------------

Clique no link **Adicionar uma nova ação automática**.

![ação Automatique](/images/v1/automatic-action-creation.png)

1.  Escolha uma ação
2.  Selecione um evento
3.  Definir os parâmetros

Ações disponíveis
-----------------

-   Criar um comentário de um provedor externo
-   Adicionar um log de comentários ao mover a tarefa entre colunas
-   Atribuir automaticamente uma categoria com base em uma cor
-   Alterar a categoria com base em um rótulo externo
-   Atribuir automaticamente uma categoria com base em um link
-   Atribuir automaticamente uma cor com base em uma categoria
-   Atribuir uma cor quando a tarefa é movida para uma coluna específica
-   Alterar cor da tarefa ao usar um link de tarefa específico
-   Atribuir uma cor a um usuário específico
-   Atribuir a tarefa à pessoa que faz a ação
-   Atribuir a tarefa à pessoa que faz a ação quando a coluna foi
    modificada
-   Atribuir a tarefa a um usuário específico
-   Alterar o responsável com base em um nome de usuário externo
-   Feche a tarefa
-   Fechar uma tarefa em uma coluna específica
-   Crie uma tarefa de um provedor externo
-   Duplicar a tarefa para outro projeto
-   Envie uma tarefa por email para alguém
-   Mova a tarefa para outro projeto
-   Mova a tarefa para outra coluna quando atribuída a um usuário
-   Mova a tarefa para outra coluna quando a categoria for alterada
-   Mover a tarefa para outra coluna quando o responsável for limpo
-   Abra uma tarefa
-   Atualizar automaticamente a data de início

Exemplos
--------

Aqui estão alguns exemplos usados ​​na vida real:

### Quando movo uma tarefa para a coluna "Concluído", fecho esta tarefa automaticamente

-   Escolha uma ação: **Feche uma tarefa em uma coluna específica**
-   Escolha o evento: **Mova uma tarefa para outra coluna**
-   Definir parâmetro de ação: **Coluna = Feito** (esta é a coluna
    destino)

### Quando movo uma tarefa para a coluna "Para ser validado", atribui essa tarefa a um usuário específico

-   Escolha a ação: **Atribuir a tarefa a um usuário específico**
-   Escolha o evento: **Mova uma tarefa para outra coluna**
-   Definir os parâmetros de ação: **Coluna = Para ser validado** e
    **Usuário = Bob** (Bob é nosso testador)

### Quando movo uma tarefa para a coluna "Trabalho em andamento", atribuo essa tarefa ao usuário atual

-   Escolha a ação: **Atribuir a tarefa à pessoa que realiza a ação
    quando a coluna é alterada**
-   Escolha o evento: **Mova uma tarefa para outra coluna**
-   Definir parâmetro de ação: **Coluna = trabalho em andamento**

### Quando uma tarefa é concluída, duplique essa tarefa para outro projeto

Digamos que temos dois projetos: "Pedidos do cliente" e "Produção".
Uma vez o pedido é validado, troque-o para o projeto "Produção".

-   Escolha uma ação: **Duplique a tarefa para outro projeto**
-   Escolha o evento: **Fechando uma tarefa**
-   Definir parâmetros de ação: **Coluna = Validado** e **Projeto =
    Produção**

### Quando uma tarefa é movida para a última coluna, mova exatamente a mesma tarefa para outro projeto

Digamos que temos dois projetos: "ideias" e "desenvolvimento". Uma
vez que a ideia é validado, troque-o para o projeto "Desenvolvimento".

-   Escolha uma ação: **Mova a tarefa para outro projeto**
-   Escolha o evento: **Mova uma tarefa para outra coluna**
-   Definir parâmetros de ação: **Coluna = Validado** e **Projeto
    = Desenvolvimento**

### Eu quero atribuir automaticamente uma cor ao usuário Bob

-   Escolha uma ação: **Atribuir uma cor a um usuário específico**
-   Escolha o evento: **Alteração do responsável da tarefa**
-   Definir parâmetros de ação: **Cor = Verde** e **Designação = Bob**

### Quero atribuir uma cor automaticamente à categoria definida "Solicitação de recurso"

-   Escolha uma ação: **Atribuir automaticamente uma cor com base em uma
    categoria**
-   Escolha o evento: **Criação ou modificação de tarefas**
-   Definir parâmetros de ação: **Cor = Azul** e **Categoria =
    Solicitação de funcionalidade**

### Desejo definir a data de início automaticamente quando a tarefa for movida para a coluna "Trabalho em andamento"

-   Escolha uma ação: **Atualizar automaticamente a data de início**
-   Escolha o evento: **Mova uma tarefa para outra coluna**
-   Definir parâmetros de ação: **Coluna = trabalho em andamento**
