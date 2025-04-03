---
title: Assinaturas do iCalendar
menu:
    main:
        parent: Guia do Usuário
---

Kanboard suporta feeds do iCal para projetos e usuários. Esse recurso
permite que você importe tarefas do Kanboard em praticamente qualquer
programa de calendário (por exemplo Microsoft Outlook, Apple Calendar,
Mozilla Thunderbird e Google Calendário).

As assinaturas de calendário são de acesso **somente leitura**, você não
pode criar tarefas a partir do software de calendário externo. A
exportação do feed Calendário segue o padrão iCal.

Nota: apenas as tarefas dentro do intervalo de datas de -2 meses a +6
meses são exportadas para o feed do iCalendar.

Calendários de Projetos
-----------------------

-   Cada projeto tem seu próprio calendário.
-   O link de assinatura é único por projeto, o link é ativado quando
    você ativa o acesso público do seu projeto: **Configurações do projeto > Acesso público**.
-   Este calendário mostra apenas tarefas para o projeto selecionado.

Calendários de Usuários
-----------------------

-   Cada usuário tem seu próprio calendário.
-   O link de assinatura é único por usuário, o link é ativado
    quando você ativa o acesso público do seu usuário: **Perfil do
    usuário > Acesso público**.
-   Este calendário mostra tarefas atribuídas ao usuário para todos os
    projetos.

Adicionando o Calendário do Kanboard ao Calendário da Apple
-----------------------------------------------------------

-   Abrir calendário
-   Selecione **Arquivo > Nova Inscrição no Calendário**
-   Copie e cole o URL do feed iCal da Kanboard

![adicionar assinatura do iCal](/images/v1/apple-calendar-add-subscription.png)

-   Você pode optar por sincronizar o calendário com o iCloud para ser
    disponível em todos os seus dispositivos
-   Não se esqueça de selecionar a frequência de atualização

![Editar assinatura do iCal](/images/v1/apple-calendar-edit-subscription.png)

Adicionando o Calendário do Kanboard ao Mozilla Thunderbird
-----------------------------------------------------------

-   Instale o complemento **Lightning** para adicionar suporte de
    calendário ao Thunderbird
-   Clique em **Arquivo > Novo Calendário**
-   Na caixa de diálogo, escolha **Na rede**

![Thunderbird Passo 1](/images/v1/thunderbird-new-calendar-step1.png)

-   Escolha o formato iCalendar
-   Copie e cole o URL do feed iCal da Kanboard

![Passo 2 do Thunderbird](/images/v1/thunderbird-new-calendar-step2.png)

-   Escolha as cores e outras configurações e, finalmente, salve

Adicionando seu calendário do Kanboard ao Google Agenda
-------------------------------------------------------

-   Clique na seta para baixo ao lado de **Outras agendas**.
-   Selecione **Adicionar por URL** no menu.
-   Copie e cole o URL do feed iCal da Kanboard

![Google Agenda](/images/v1/google-calendar-add-subscription.png)

Seu calendário Kanboard também pode estar disponível no seu dispositivo
Android se você habilita a sincronização.

Nota: de acordo com o Suporte do Google, os calendários externos não são
atualizados com muita frequência, [leia a
documentação](https://support.google.com/calendar/answer/37100?hl=pt&ref_topic=1672445).
