---
title: Proje Ayarları
toc: true
menu:
    main:
        parent: Kullanici rehberi
---

Sağ üstte bulunan **Ayarlar** menüsüne gidin ve ardından soldaki **Proje ayarları** seçeneğini seçin.

![Project settings](/images/v1/project-settings.png)

### Yeni Projeler İçin Varsayılan Sütunlar

Varsayılan sütun adlarını buradan değiştirebilirsiniz.
Her zaman aynı sütunlara sahip projeler oluşturmanız faydalı olabilir.

Her sütun adı virgülle ayrılmalıdır.

Varsayılan olarak, Kanboard şu sütun adlarını kullanır: Bekleme Listesi (Backlog), Hazır, İşlemde ve Tamamlandı.

### Yeni Projeler İçin Varsayılan Kategoriler

Kategoriler uygulama genelinde değil, projelere özeldir.
Her proje farklı kategorilere sahip olabilir.

Ancak, tüm projeleriniz için aynı kategorileri oluşturmayı tercih ediyorsanız, burada otomatik olarak oluşturulacak kategorilerin listesini tanımlayabilirsiniz.

### Bir Kullanıcının Aynı Anda Yalnızca Bir Alt Görev Almasına İzin Ver

Bu seçenek etkinleştirildiğinde, bir kullanıcı aynı anda yalnızca bir alt görev üzerinde çalışabilir.

Başka bir alt görev "devam ediyor" durumundaysa, kullanıcı şu iletişim kutusunu görür:

![Subtask user restriction](/images/v1/subtask-user-restriction.png)

### Alt Görev Zaman İzlemeyi Otomatik Olarak Tetikleme

- Bu seçenek etkinleştirilirse, bir alt görevin durumu "devam ediyor" olarak değiştirildiğinde zamanlayıcı otomatik olarak başlar.
- Zaman izlemeyi kullanmıyorsanız, bu seçeneği devre dışı bırakabilirsiniz.

### Kümülatif Akış Diyagramında Kapalı Görevleri Dahil Et

- Bu seçenek etkinleştirilirse, kapalı görevler kümülatif akış şemasına dahil edilir.
- Bu seçenek devre dışı bırakılırsa, yalnızca açık görevler dahil edilir.
- Bu seçenek, tablonun "toplam" sütununu etkiler: "project_daily_column_stats".
