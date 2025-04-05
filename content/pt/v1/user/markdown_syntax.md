---
title: Sintaxe do Markdown
menu:
    main:
        parent: Guia do Usuário
---

O Kanboard utiliza a [Sintaxe Markdown](http://en.wikipedia.org/wiki/Markdown) para comentários ou
descrições de tarefas. Aqui estão alguns exemplos:

Negrito e Itálico
-----------------

-   Texto em negrito: use 2 asteriscos ou 2 sublinhados.
-   Texto em itálico: use 1 asterisco ou 1 sublinhado.

    Esta **palavra** é muito __importante__.

    E aqui, uma palavra em *itálico* com _sublinhado_.

Listas Não Ordenadas
--------------------

Listas não ordenadas podem usar asteriscos, hífens ou sinais de mais.

    - Item 1
    - Item 2
    - Item 3

    ou

    * Item 1
    * Item 2
    * Item 3

Listas Ordenadas
----------------

Listas ordenadas são prefixadas por números, como neste exemplo:

    1. Faça isso primeiro.
    2. Faça isso.
    3. E isso.

Links
-----

    [Título do meu link](https://kanboard.org/)

    <https://kanboard.org>

Código Fonte
------------

### Código Embutido

Use uma crase.

    Execute este comando: `tail -f /var/log/messages`.

### Blocos de Código

Use 3 crases, opcionalmente com o nome da linguagem.

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
