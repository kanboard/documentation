---
title: Projetos
menu:
    main:
        parent: Guia do Usuário
---

Tipos de Projeto
----------------

Existem dois tipos de projetos:

Tipo              | Descrição
------------------| ----------------------------------------------------
Projeto de equipe | Projeto com gerenciamento de usuários e grupos.
Projeto Privado   | Projeto que pertence a apenas uma pessoa, sem gerenciamento de usuários.

-   Somente administradores e gerentes do aplicativo podem criar projetos de equipe.
-   Projetos privados podem ser criados por qualquer pessoa.

Criando Projetos
----------------

Kanboard pode lidar com vários projetos.

### Criando projetos para vários usuários

-   Somente administradores e gerentes podem criar esses projetos.
-   Gerenciamento de usuários está disponível.

No painel, clique no link **Novo projeto**:

![Formulário de criação do projeto](/images/v1/new-project.png)

É muito fácil: basta encontrar um nome para o seu projeto!

### Criando um projeto privado

-   Qualquer pessoa pode criar um projeto privado.
-   **NÃO** há gerenciamento de usuários.
-   Somente o proprietário e administradores podem acessar o projeto.

No painel, clique no link **Novo projeto privado**.

### Criando projetos a partir de outro projeto

Quando você cria um novo projeto, pode optar por duplicar as
propriedades de outro projeto:

-   Permissões
-   Ações
-   Raias
-   Categorias
-   Tarefas

Editando Projetos
-----------------

Projetos podem ser modificados a qualquer momento.

Para renomear um projeto, basta clicar no link intitulado **"Editar
projeto"** à esquerda.

![edição do projeto](/images/v1/project-edition.png)

-   A data de início e de término são usadas para gerar o gráfico de
    Gantt do projeto.
-   A descrição é visível como uma dica no quadro e na página de
    listagem de projetos.
-   Administradores e administradores de projetos podem converter um
    projeto privado em um projeto de múltiplos usuários, alterando a caixa de
    seleção "Projeto privado".
-   Você também pode converter um projeto de vários usuários em um
    projeto privado.

Nota: Quando você torna um projeto privado, todos os usuários existentes
ainda terão acesso ao projeto. Você deve ajustar a lista de usuários de
acordo às suas necessidades.

Removendo Projetos
------------------

Para remover um projeto, você deve ser o gerente do projeto ou um
administrador.

Vá para o **"Configurações do projeto"** e, no menu à esquerda, na
parte inferior, escolha **"Remover"**.

![Removendo Projetos](/images/v1/project-remove.png)

A remoção de um projeto remove todas as tarefas que pertencem a este
projeto.

Permissões do Projeto
---------------------

Cada projeto é isolado de outros projetos. O acesso ao projeto deve ser
permitido pelo proprietário do projeto.

Cada usuário e cada grupo pode ter uma função diferente designada.
Existem 3 tipos de papéis para projetos:

-   Gestor de projeto
-   Membro do projeto
-   Visualizador de Projetos

Somente administradores têm acesso a tudo.

As atribuições de função são visíveis em **Configurações do projeto\>
Permissões**:

![permissões do projeto](/images/v1/project-permissions.png)

Projetos privados não podem definir permissões.

Funções personalizadas do projeto
---------------------------------

Você pode criar funções de projeto personalizadas para aplicar um
conjunto de restrições específicas sobre as pessoas que pertencem a este
papel. Esses papéis personalizados são definidos para cada projeto.

Um papel personalizado herda do papel membro do projeto. Por exemplo,
você pode querer criar um papel personalizado para forçar alguém a
seguir um processo. Você pode ter um grupo de pessoas com permissão para
transferir tarefas apenas da coluna "Trabalho em progresso" para a
coluna "Concluído".

### Restrições Disponíveis

-   Restrições de Projeto:
    -   Criação de tarefa não é permitida
    -   Fechar ou abrir uma tarefa não é permitido
    -   Mover uma tarefa não é permitido
-   Restrições de Colunas:
    -   A criação de tarefas é **permitida** apenas para uma coluna
        específica
    -   A criação de tarefas é **bloqueada** apenas para uma coluna
        específica
    -   Fechar ou abrir uma tarefa é **permitida** apenas para uma
        determinada coluna
    -   Fechar ou abrir uma tarefa é **bloqueada** apenas para uma
        determinada coluna
-   Mover tarefas apenas entre colunas especificadas

### Configuração

#### 1) Crie um novo papel personalizado

A partir das configurações do projeto, clique à esquerda no menu
**Funções Personalizadas** e, na parte superior da página, clique em
**Adicionar uma nova função personalizada**.

![novo papel personalizado](/images/v1/new_custom_role.png)

Dê um nome à função e envie o formulário.

#### 2) Adicione uma restrição ao papel

Existem diferentes tipos de restrições:

-   Restrições do projeto
-   Arrastar e soltar restrições
-   Restrições de coluna

Você pode clicar no menu suspenso da tabela para adicionar uma nova
restrição:

![adicionar uma nova restrição](/images/v1/add_new_restriction.png)

#### 3) Lista de restrições

![lista de restrições](/images/v1/example-restrictions.png)

Por exemplo, esse papel é capaz de criar tarefas apenas na coluna
"Backlog" e para mover tarefas entre a coluna "A fazer" e "Em
andamento".

#### 4) Atribuir um papel a alguém

Vá para a seção \"permissões\" no menu à esquerda e atribua o papel
desejado ao usuário.

![função de projeto personalizada](/images/v1/custom_roles.png)

### Exemplos

#### Permitir que as pessoas criem tarefas apenas em colunas específicas

![Exemplo de criação de tarefas de restrição](/images/v1/example-restriction-task-creation.png)

-   Usuários que pertencem a essa função só poderão criar novas
    tarefas na coluna "Backlog".
-   A combinação das duas regras é importante, caso contrário, isso não
    funciona.

#### Permitir que as pessoas alterem o status da tarefa apenas em colunas específicas

![Exemplo de status da tarefa de restrição](/images/v1/example-restriction-task-status.png)

-   Usuários que pertencem a essa função poderão alterar o status da
    tarefa na coluna "Backlog".
-   Tarefas com o status aberto são visíveis no quadro e tarefas com o
    status fechado estão ocultas por padrão no quadro.

#### Não permitir que pessoas alterem o status da tarefa em uma coluna específica

![Exemplo de restrição de coluna](/images/v1/example-restriction-task-status-blocked.png)

Os usuários que pertencem a essa função não poderão alterar o status da
tarefa na coluna "Concluído". No entanto, isso será possível em outras
colunas.

#### Permitir que as pessoas movam tarefas apenas entre colunas específicas

![Exemplo arrastar e soltar tarefa de restrição](/images/v1/example-restriction-task-drag-and-drop.png)

Os usuários que pertencem a essa função poderão mover tarefas apenas
entre coluna "Pronto" e "Trabalho em andamento".

Compartilhando Painéis e Tarefas
--------------------------------

Por padrão, os quadros são privados, mas é possível tornar um quadro
público.

Um quadro público **não pode ser modificado: ele tem acesso somente
leitura**. O acesso é protegido por um token aleatório. Somente pessoas
que têm o URL correto podem ver o quadro.

Quadros públicos são atualizados automaticamente a cada 60 segundos. Os
detalhes da tarefa também estão disponíveis no modo somente leitura.

Exemplos de uso:

-   Compartilhe seu quadro com alguém de fora da sua organização
-   Exibir o quadro em uma tela grande em seu escritório

### Ativar acesso público

Selecione o seu projeto, clique em **"Acesso público"** e, finalmente,
clique no botão **"Ativar acesso público"**.

![ativar o acesso público](/images/v1/project-enable-sharing.png)

Quando o acesso público está ativado, alguns links são gerados:

-   Vista do quadro público
-   link de subscrição de feeds RSS
-   link de assinatura do iCalendar

![desativar o acesso público](/images/v1/project-disable-sharing.png)

Você também pode desativar o acesso público sempre que quiser.

Sempre que você ativa ou desativa o acesso público, um novo token
aleatório é gerado. **Os links anteriores não funcionam mais**!

Filtros Personalizados
----------------------

Filtros personalizados permitem que você salve qualquer consulta de
pesquisa. Desta forma, você pode estender os filtros padrão facilmente e
salve as consultas de pesquisa mais usadas.

-   Filtros personalizados são armazenados por projeto e associados ao
    criador.
-   Se o criador for gerente de projeto, ele pode optar por compartilhar
    o filtro com outros membros do projeto.

### Criação de Filtro

Vá para o menu suspenso de ação ou nas configurações do projeto e
escolha **filtros personalizados**:

![criação de filtro personalizado](/images/v1/custom-filter-creation.png)

Depois de criar seu filtro, ele aparecerá no quadro ao lado dos filtros
padrão:

![lista suspensa do filtro personalizado](/images/v1/custom-filter-dropdown.png)
