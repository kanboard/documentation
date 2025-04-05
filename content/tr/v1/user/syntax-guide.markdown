---
title: Sözdizimi Kılavuzu
toc: true
menu:
    main:
        parent: Kullanici rehberi
---

Kanboard, yorumlar veya görev açıklamaları için [Markdown Sözdizimi](http://en.wikipedia.org/wiki/Markdown) kullanır.
İşte bazı örnekler:

Kalın ve İtalik
---------------

- Kalın metin: 2 yıldız veya 2 alt çizgi kullanın.
- İtalik metin: 1 yıldız veya 1 alt çizgi kullanın.

```
Bu **kelime** çok __önemlidir__.

Ve burada, bir *italik* bir kelime; bir _alt çizgi_ ile.
```

Sırasız Listeler
----------------

Sırasız listelerde yıldız, eksi veya artılar kullanabilirsiniz.

```
- Öğe 1
- Öğe 2
- Öğe 3

veya

* Öğe 1
* Öğe 2
* Öğe 3
```

Sıralı Listeler
---------------

Sıralı listeler şöyle bir sayı önekiyle oluşturulur:

```
1. Önce bunu yap
2. Sonra bunu yap
3. Ve ardından şunu yap
```

Bağlantılar
-----------

```
[Bağlantı başlığım](https://kanboard.org/)

<https://kanboard.org>
```

Kaynak Kod
----------

### Satır İçi Kod

Geri tırnak işareti (backtick) kullanın.

```
Bu komutu çalıştır: `tail -f /var/log/messages`.
```

### Kod Blokları

Sonunda dil adıyla birlikte 3 geri tırnak işareti kullanın.

````php
<?php

phpinfo();

?>
````

Başlıklar
---------

```
# Başlık Düzeyi 1

## Başlık Düzeyi 2

### Başlık Düzeyi 3
```
