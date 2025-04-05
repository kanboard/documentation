---
title: Assinaturas do iCalendar
menu:
    main:
        parent: Guia do Usuário
---

O Kanboard suporta feeds do iCal para projetos e usuários. Esse recurso
permite que você importe tarefas do Kanboard em praticamente qualquer
programa de calendário (por exemplo, Microsoft Outlook, Apple Calendar,
Mozilla Thunderbird e Google Calendar).

As assinaturas de calendário são de acesso **somente leitura**. Você não
pode criar tarefas a partir de um software de calendário externo. A
exportação do feed de calendário segue o padrão iCal.

Nota: Apenas as tarefas dentro do intervalo de datas de -2 meses a +6
meses são exportadas para o feed do iCalendar.

Calendários de Projetos
-----------------------

-   Cada projeto tem seu próprio calendário.
-   O link de assinatura é único para cada projeto e é ativado quando
    você habilita o acesso público do projeto: **Configurações do projeto > Acesso público**.
-   Este calendário mostra apenas as tarefas do projeto selecionado.

Calendários de Usuários
-----------------------

-   Cada usuário tem seu próprio calendário.
-   O link de assinatura é único para cada usuário e é ativado
    quando você habilita o acesso público do usuário: **Perfil do
    usuário > Acesso público**.
-   Este calendário mostra as tarefas atribuídas ao usuário em todos os
    projetos.

Adicionando o Calendário do Kanboard ao Apple Calendar
------------------------------------------------------

-   Abra o Apple Calendar.
-   Selecione **Arquivo > Nova Inscrição no Calendário**.
-   Copie e cole o URL do feed iCal do Kanboard.

![Adicionar assinatura do iCal](/images/v1/apple-calendar-add-subscription.png)

-   Você pode optar por sincronizar o calendário com o iCloud para que
    ele esteja disponível em todos os seus dispositivos.
-   Não se esqueça de selecionar a frequência de atualização.

![Editar assinatura do iCal](/images/v1/apple-calendar-edit-subscription.png)

Adicionando o Calendário do Kanboard ao Mozilla Thunderbird
-----------------------------------------------------------

-   Instale o complemento **Lightning** para adicionar suporte a
    calendários no Thunderbird.
-   Clique em **Arquivo > Novo Calendário**.
-   Na caixa de diálogo, escolha **Na rede**.

![Thunderbird Passo 1](/images/v1/thunderbird-new-calendar-step1.png)

-   Escolha o formato iCalendar.
-   Copie e cole o URL do feed iCal do Kanboard.

![Thunderbird Passo 2](/images/v1/thunderbird-new-calendar-step2.png)

-   Escolha as cores e outras configurações e, finalmente, salve.

Adicionando o Calendário do Kanboard ao Google Calendar
-------------------------------------------------------

-   Clique na seta para baixo ao lado de **Outras agendas**.
-   Selecione **Adicionar por URL** no menu.
-   Copie e cole o URL do feed iCal do Kanboard.

![Google Calendar](/images/v1/google-calendar-add-subscription.png)

Seu calendário Kanboard também pode estar disponível no seu dispositivo
Android se você habilitar a sincronização.

Nota: De acordo com o suporte do Google, os calendários externos não são
atualizados com muita frequência. [Leia a documentação](https://support.google.com/calendar/answer/37100?hl=pt&ref_topic=1672445).
