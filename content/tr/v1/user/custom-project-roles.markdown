---
title: Özel Proje Rolleri
toc: true
menu:
    main:
        parent: Kullanici rehberi
---

Bu role ait kişiler üzerinde belirli kısıtlamalar dizisi uygulamak için özel proje rolleri oluşturabilirsiniz.
Bu özel roller her proje için tanımlanmıştır.

Özel rol, proje üyesi rolünden devralır.
Örneğin, birini bir işlemi takip etmeye zorlamak için özel bir rol oluşturmak isteyebilirsiniz.
Görevleri yalnızca "Devam etmekte olan iş" sütunundan "Bitti" sütununa taşımanıza izin verilen bir grup insana sahip olabilirsiniz.

Mevcut Kısıtlamalar
-------------------

- Proje Kısıtlamaları:
    - Görev oluşturulmasına izin verilmez.
    - Bir görevi kapatmak veya açmak yasaktır.
    - Görevin taşınmasına izin verilmez.
- Sütun Kısıtlamaları:
    - Görev oluşturulması yalnızca belirli bir sütun için **izin** verilir.
    - Görev oluşturulması yalnızca belirli bir sütun için **engellenir**.
    - Bir görevi kapatmak veya açmak yalnızca belirli bir sütuna **izin** verilir.
    - Bir görevi kapatmak veya açmak yalnızca belirli bir sütun için **engellenir**.
- Görevleri yalnızca belirtilen sütunlar arasında taşıma.

Yapılandırma
------------

### 1) Yeni Bir Özel Rol Oluştur

Proje ayarlarından, **Özel Roller** menüsünde soldaki simgeye tıklayın ve sayfanın üst kısmında **Yeni özel rol ekleyin** seçeneğini tıklayın.

![New custom role](/images/v1/new_custom_role.png)

Rol için bir isim verin ve formu gönderin.

### 2) Rol İçin Bir Sınırlama Ekleyin

Burada farklı kısıtlamalar vardır:

- Proje kısıtlamaları
- Sürükle ve bırak kısıtlamaları
- Sütun kısıtlamaları

Yeni bir kısıtlama eklemek için tabloda açılır menüye tıklayabilirsiniz:

![Add a new restriction](/images/v1/add_new_restriction.png)

### 3) Kısıtlamalar Listesi

![List of restrictions](/images/v1/example-restrictions.png)

Örneğin, bu rol yalnızca "Geri Kayıt-Backlog" sütununda görevler oluşturabilir ve görevleri "Hazır" ve "Devam etmekte olan" sütunları arasında taşımak mümkündür.

### 4) Rolü Birine Atayın

Sol menüdeki "İzinler" bölümüne gidin ve istenen rolü kullanıcıya atayın.

![Custom project role](/images/v1/custom_roles.png)

Örnekler
--------

### Kullanıcıların Yalnızca Belirli Sütunlarda Görev Oluşturmasına İzin Ver

![Example restriction task creation](/images/v1/example-restriction-task-creation.png)

- Bu role ait kullanıcılar, yalnızca "Geri Kayıt-Backlog" sütununda yeni görevler oluşturabilir.
- 2 kuralın kombinasyonu önemlidir, aksi takdirde bu işe yaramaz.

### Kullanıcıların Görev Durumunu Yalnızca Belirli Sütunlarda Değiştirmelerine İzin Ver

![Example restriction task status](/images/v1/example-restriction-task-status.png)

- Bu role ait olan kullanıcılar, "Geri Kayıt-Backlog" sütunundaki görev durumunu değiştirebilecek.
- Durum açık olan görevler tahta üzerinde görünür ve durum kapalı olan görevler varsayılan olarak tahtada gizlidir.

### Kullanıcıların Belirli Bir Sütundaki Görev Durumunu Değiştirmesine İzin Verme

![Example column restriction](/images/v1/example-restriction-task-status-blocked.png)

Bu role ait kullanıcılar, "Tamamlandı" sütunundaki görev durumunu değiştiremez.
Ancak diğer sütunlarda bu mümkün olacaktır.

### Kullanıcıların Görevleri Yalnızca Belirli Sütunlar Arasında Taşımasına İzin Ver

![Example restriction task drag and drop](/images/v1/example-restriction-task-drag-and-drop.png)

Bu role ait kullanıcılar, görevleri yalnızca "Hazır" ve "Devam etmekte olan" sütunları arasında taşıyabilir.
