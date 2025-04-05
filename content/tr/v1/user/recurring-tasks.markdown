---
title: Tekrar Eden Görevler
toc: true
menu:
    main:
        parent: Kullanici rehberi
---

Kanban metodolojisine uymak için, tekrar eden görevler bir tarih tabanında değil, panodaki olaylara dayanır.

- Seçilen olaylar gerçekleştiğinde, tekrar eden görevler panonun ilk sütununa kopyalanır.
- Teslim tarihi otomatik olarak yeniden hesaplanabilir.
- Her görev, onu oluşturan üst görevin görev no'sunu (ID) ve oluşturulmuş alt görevin kaydını tutar.

Yapılandırma
------------

Görev görünüm sayfasına gidin veya panodaki açılır menüyü kullanın, ardından **Tekrarı düzenleyin** seçeneğini belirleyin.

![Recurring task](/images/v1/recurring-tasks.png)

Şu anda yeni tekrar eden bir görev oluşturan 3 tetikleyici vardır:

- Bir görevi ilk sütundan taşıma.
- Görevin son sütuna taşınması.
- Görevi kapatma.

Son tarihler mevcut görev üzerinde ayarlanmışsa, verilen gün, ay veya yıl faktörü ile yeniden hesaplanabilir.
Yeni vade tarihinin hesaplanması için temel tarih, mevcut vade tarihi veya işlem tarihi olabilir.
