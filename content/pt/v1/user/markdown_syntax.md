---
title: Sintaxe do Markdown
menu:
    main:
        parent: Guia do Usuário
---

O Kanboard usa a [Sintaxe Markdown](http://en.wikipedia.org/wiki/Markdown) para comentários ou
descrições de tarefas. Aqui estão alguns exemplos:

Negrito e itálico
-----------------

-   Texto em negrito: use 2 asteriscos ou 2 sublinhados
-   Texto em itálico: use 1 asterisco ou 1 sublinhado

    Essa **palavra** é muito __importante__ .

    E aqui, uma palavra em *itálico* com _sublinhado_.

Listas não ordenadas
--------------------

Lista não ordenada pode usar asteriscos, menos ou mais.

    - Item 1
    - Item 2
    - Item 3

    ou

    * Item 1
    * Item 2
    * Item 3

Listas ordenadas
----------------

Listas ordenadas são prefixadas por um número como esse:

    1. Faça isso primeiro
    2. Faça isso
    3. E isso

Links
-----

    [Título do meu link](https://kanboard.org/)

    <https://kanboard.org>

Código fonte
------------

### Código embutido

Use uma crase.

    Execute este comando: `tail -f /var/log/messages`.

### Blocos de Código

Use 3 crases com eventualmente o nome da linguagem.

    ```php
    <?php

    phpinfo();

    ?>
    ```

Títulos
-------

    # Nível de título 1

    ## Nível de título 2

    ### Nível de título 3
