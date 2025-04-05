---
title: Usuários e Grupos
menu:
    main:
        parent: Guia do Usuário
---

Tipos de Usuários
-----------------

No Kanboard, existem dois tipos de usuários:

Tipo           | Descrição
---------------| ----------------------------------------------------------
Usuário Local  | Usuário que armazena sua senha no banco de dados do Kanboard.
Usuário Remoto | As credenciais do usuário são gerenciadas por outro sistema (exemplo: Servidor LDAP).

Exemplos de usuários remotos:

-   Usuário LDAP.
-   Usuários autenticados por um proxy reverso.
-   Usuários do OAuth2.

Funções do usuário
------------------

### Papéis na Aplicação

Cada usuário do Kanboard possui uma das seguintes funções:

Papel                              | Descrição
-----------------------------------| -----------------------------------
Administrador                      | Acesso a tudo.
Gerente                            | Pode criar projetos de equipe, mas não pode alterar as configurações da aplicação.
Usuário                            | Pode criar apenas projetos privados.

### Papéis do Projeto

Cada projeto de equipe individual pode atribuir uma função diferente a
cada usuário ou grupo:

Papel                   | Descrição
------------------------| --------------------------------------------------------
Gerente de Projeto      | Pode alterar as configurações do projeto, acessar o gráfico de Gantt e relatórios.
Membro de Projeto       | Pode criar tarefas e usar o quadro.
Visualizador do Projeto | Acesso somente leitura ao quadro e às tarefas.

As funções de projeto personalizadas podem ser criadas para aplicar um
conjunto de restrições aos usuários.

Gestão de Grupos
----------------

No Kanboard, cada usuário pode ser membro de um ou vários grupos. Um
grupo é como uma equipe ou uma organização.

Somente administradores podem criar novos grupos e atribuir usuários.

Os grupos podem ser gerenciados em **Gestão dos usuários \> Ver todos os
grupos**. A partir dessa página, você pode criar grupos e atribuir usuários.

![Gestão de Grupos](/images/v1/groups-management.png)

Cada gerente de projeto pode autorizar o acesso a um conjunto de grupos
na página de permissões do projeto.

O ID externo é usado principalmente para provedores de grupos externos.
O Kanboard fornece um provedor de grupo LDAP para sincronizar
automaticamente grupos dos servidores LDAP.

Adicionar um novo usuário
-------------------------

Para adicionar um novo usuário, você deve ser um administrador.

1.  No menu suspenso, no canto superior direito, vá para o menu **Gestão
    dos usuários**.
2.  Na parte superior, clique no link **Novo usuário local** ou **Novo
    usuário remoto**.
3.  Preencha o formulário e salve.

![Novo usuário](/images/v1/new-user.png)

Ao criar um **usuário local**, você precisa especificar pelo menos os
seguintes valores:

-   **Nome de usuário**: este é o identificador exclusivo do seu usuário
    (login).
-   **Senha**: a senha do usuário deve ter pelo menos 6 caracteres.

Para **usuários remotos**, apenas o nome de usuário é obrigatório.

Editar usuários
---------------

Quando você acessa o menu **Usuários**, verá a lista de usuários.
Para modificar um usuário, clique no link **Editar**.

-   Se você for um usuário regular, poderá alterar apenas o seu próprio
    perfil.
-   Você precisa ser um administrador para editar qualquer usuário.

Remover usuários
----------------

No menu **Usuários**, clique no link **Remover**. Este link é visível
apenas se você for administrador.

Se você remover um usuário específico, **as tarefas atribuídas a essa
pessoa serão desatribuídas** após a operação.

Autenticação em dois fatores
----------------------------

Cada usuário pode habilitar a [autenticação de dois
fatores](http://en.wikipedia.org/wiki/Two_factor_authentication). Após
um login bem-sucedido, um código único (6 caracteres) será solicitado ao
usuário para permitir acesso ao Kanboard.

Este código deve ser fornecido por um software compatível, normalmente
instalado em seu smartphone ou em um dispositivo diferente.

O Kanboard usa o [Algoritmo de Senha Única baseado em
Tempo](http://en.wikipedia.org/wiki/Time-based_One-time_Password_Algorithm)
definido no [RFC 6238](http://tools.ietf.org/html/rfc6238).

Existem muitos softwares compatíveis com o sistema TOTP padrão. Por
exemplo, você pode usar estes aplicativos:

-   [Google
    Authenticator](https://github.com/google/google-authenticator/)
    (Android, iOS, Blackberry).
-   [FreeOTP](https://freeotp.github.io/) (Android, iOS).
-   [OATH Toolkit](http://www.nongnu.org/oath-toolkit/) (Utilitário de
    linha de comando no Unix/Linux).

Este sistema pode funcionar offline, e você não precisa necessariamente
ter um celular.

### Configuração

1.  Vá para o seu perfil de usuário.
2.  À esquerda, clique em **Autenticação em Dois Fatores** e clique no
    botão.
3.  Uma chave secreta será gerada para você.

![2FA](/images/v1/2fa.png)

-   Você deve salvar a chave secreta no seu software TOTP. Se você
    usar um smartphone, a solução mais fácil é digitalizar o código QR
    com FreeOTP ou Google Authenticator.
-   Cada vez que você abrir uma nova sessão, um novo código será
    solicitado.
-   Não se esqueça de testar seu dispositivo antes de fechar sua sessão.

Uma nova chave secreta será gerada toda vez que você ativar ou desativar
esse recurso.
