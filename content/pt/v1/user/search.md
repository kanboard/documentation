---
title: Sintaxe para Pesquisa Avançada
---

O Kanboard usa uma linguagem de consulta simples para pesquisa avançada.
Você pode pesquisa em tarefas, comentários, subtarefas, links, mas
também na atividade corrente.

Exemplo de consulta
-------------------

Este exemplo retornará todas as tarefas atribuídas a mim com uma data de
vencimento de amanhã e um título que contenha "meu título":

    assigne:me due:tomorrow meu título

Pesquisa de Projetos
--------------------

### Pesquisar por id ou título da tarefa

-   Pesquisa por id de tarefa: `# 123`
-   Pesquisa por id de tarefa e título da tarefa: `123`
-   Pesquisar por título da tarefa: qualquer coisa que não corresponda a
    nenhuma pesquisa de atributos

### Pesquisar por status

Atributo: **status**

-   Consulta para encontrar tarefas abertas: `status: open`
-   Consulta para encontrar tarefas fechadas: `status: closed`

### Pesquisar por designação

Atributo: **assignee**

-   Consulta com o nome completo: `assignee: "Frederic Guillot"`
-   Consulta com o nome de usuário: `assignee: fguillot`
-   Consulta de múltiplos usuários:
    `assignee: user1 assignee: "John Doe"`
-   Consulta para tarefas não atribuídas: `assignee: nobody`
-   Consulta para minhas tarefas atribuídas: `assignee: me`

### Pesquisar pelo criador da tarefa

Atributo: **creator**

-   Tarefas criadas por mim: `creator: me`
-   Tarefas criadas por John Doe: `creator: "John Doe"`
-   Tarefas criadas pelo usuário id \# 1: `creator: 1`

### Pesquisar por responsável por subtarefa

Atributo: **subtask:assignee**

-   Exemplo: `subtask:assignee:"John Doe"`

### Pesquisa por cor

Atributo: **color**

-   Consulta para pesquisar por id de cor: `color:blue`
-   Consulta para pesquisar pelo nome da cor: `color:"Deep Orange"`

### Pesquisa por data de vencimento

Atributo: **due**

-   Tarefas de pesquisa devidas hoje: `due:today`
-   Tarefas de pesquisa para amanhã: `due:tomorrow`
-   Tarefas de pesquisa devidas ontem: `due:yesterday`
-   Tarefas de pesquisa devidas com a data exata: `due:2015-06-29`
-   Tarefas de pesquisa sem uma data de vencimento: `due:none`

A data deve usar o formato ISO 8601: **AAAA-MM-DD**.

Todos os formatos de strings suportados pela função `strtotime()` são
suportados, por exemplo `next Thursday`, `-2 days`, `+2 months`,
`tomorrow`, etc.

Operadores suportados com uma data:

-   Maior que: **due:>2015-06-29**
-   Menor que: **due:<2015-06-29**
-   Maior que ou igual: **due:>=2015-06-29**
-   Menor que ou igual: **due:<=2015-06-29**

### Pesquisa por data de modificação

Atributo: **modified** ou **updated**

Os formatos de data são os mesmos que a data de vencimento.

Há também um filtro por tarefas modificadas recentemente: `due:recently`.

Esta consulta usará o mesmo valor que o período de destaque do quadro configurado nas configurações.

### Pesquisar por data de criação

Atributo: **created**

Funciona da mesma forma que as consultas de data de modificação.

### Pesquisa por data de início

Atributo: **started**

### Pesquisar por descrição

Atributo: **description** ou **desc**

Exemplo: `description:"pesquisa de texto"`

### Pesquisa por conclusão

Atributo: **completed**

### Pesquisa por referência externa

A referência da tarefa é um id externo da sua tarefa, por exemplo, um
número de bilhete de outro software.

-   Encontre tarefas com uma referência: `ref:1234` ou `reference:TICKET-1234`
-   Pesquisa de curinga: `ref:TICKET-*`

### Pesquisar por categoria

Atributo: **category**

-   Encontre tarefas com uma categoria específica: `category:"Feature Request"`
-   Encontre todas as tarefas que possuem essas categorias: `category:"Bug" category:"Melhorias"`
-   Encontre tarefas sem categoria atribuída: `category:none`

### Pesquisa por projeto

Atributo: **project**

-   Localizar tarefas por nome de projeto: `project:"nome do meu projeto"`
-   Localizar tarefas por id do projeto: `project:23`
-   Encontre tarefas para vários projetos: `project:"Meu projeto Um" projeto:"Meu projeto B"`

### Pesquisar por colunas

Atributo: **column**

-   Localizar tarefas por nome de coluna: `column:"Em progresso"`
-   Localizar tarefas para várias colunas: `column:"Backlog" column: "A Fazer"`

### Pesquisar por raia

Atributo: **swinlane**

-   Encontre tarefas por raia: `swimlane:"Version 42"`
-   Encontre tarefas em várias raias: `swimlane:"Versão 1.2" swimlane:"Versão 1.3"`

### Pesquisar por link da tarefa

Atributo: **link**

-   Localizar tarefas por nome de link: `link:"é um marco de"`
-   Encontre tarefas em vários links: `link:"é um marco de" link:"relacionado a"`

### Pesquisar por comentário

Atributo: **comment**

-   Encontre comentários que contenham este
    título: `comment:"Minha mensagem de comentário"`

### Pesquisar por etiquetas

Atributo: **tag**

-   Exemplo: `tag:"Minha etiqueta"`

### Pesquisa por pontuação/complexidade

Atributo: **score** ou **complexity**

-   `score:>=21`
-   `complexity:8`

Pesquisa de fluxo de atividade
------------------------------

### Pesquisar eventos por título da tarefa

Atributo: **title** ou nenhum (padrão)

-   Exemplo: `title:"Minha tarefa"`
-   Pesquisa por id de tarefa: `#123`

### Pesquisar eventos por status da tarefa

Atributo: **status**

### Pesquisar pelo criador do evento

Atributo: **creator**

### Pesquisar por data de criação do evento

Atributo: **created**

### Pesquisar eventos por projeto

Atributo: **project**
