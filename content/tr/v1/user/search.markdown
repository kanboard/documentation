---
title: Gelişmiş Arama Sözdizimi
toc: true
menu:
    main:
        parent: Kullanici rehberi
---

Kanboard, gelişmiş arama için basit bir sorgu dili kullanır.
Görevler, yorumlar, alt görevler, bağlantılar ve etkinlik akışında arama yapabilirsiniz.

Sorgu Örneği
------------

Bu örnek, yarın için bir bitiş tarihi ve "başlığım" kelimesini içeren bir başlık ile bana atanan tüm görevleri döndürür:

```
assignee:me due:tomorrow başlığım
```

Genel Arama
-----------

### Görev Kimliği veya Başlığa Göre Arama

- Görev kimliği ile ara: `#123`
- Görev kimliği ve başlığa göre ara: `123`
- Görev başlığına göre ara: Arama nitelikleriyle eşleşmeyen herhangi bir şey.

### Duruma Göre Ara

Özellik: **status**

- Açık görevler: `status:open`
- Kapatılan görevler: `status:closed`

### Atanan Kişiye Göre Ara

Özellik: **assignee**

- Tam adıyla: `assignee:"Frederic Guillot"`
- Kullanıcı adıyla: `assignee:fguillot`
- Birden fazla atanan: `assignee:user1 assignee:"John Doe"`
- Atanmamış görevler: `assignee:nobody`
- Kendi görevleriniz: `assignee:me`

### Görev Yaratıcısına Göre Ara

Özellik: **creator**

- Kendi oluşturduğunuz görevler: `creator:me`
- John Doe tarafından oluşturulan görevler: `creator:"John Doe"`
- Kullanıcı no #1 tarafından oluşturulan görevler: `creator:1`

### Alt Görev Atayanına Göre Ara

Özellik: **subtask:assignee**

- Örnek: `subtask:assignee:"John Doe"`

### Renge Göre Ara

Özellik: **color**

- Renk kimliğiyle: `color:mavi`
- Renk adına göre: `color:"Oranj"`

### Vadesine Göre Ara

Özellik: **due**

- Bugünkü görevler: `due:today`
- Yarınki görevler: `due:tomorrow`
- Dünkü görevler: `due:yesterday`
- Tam tarihli görevler: `due:2015-06-29`

Tarih ISO 8601 biçiminde olmalıdır: **YYYY-MM-DD**.

`strtotime()` işlevi tarafından desteklenen tüm dize formatları kullanılabilir, örneğin `next Thursday`, `-2 days`, `+2 months`, `tomorrow`, vb.

Desteklenen tarih operatörleri:

- Bundan büyük: **due:>2015-06-29**
- Bundan küçük: **due:<2015-06-29**
- Büyük veya eşit: **due:>=2015-06-29**
- Küçük veya eşit: **due:<=2015-06-29**

### Değiştirilme Tarihine Göre Ara

Özellik: **modified** veya **updated**

Tarih biçimleri vade tarihiyle aynıdır.

Yakın zamanda değiştirilmiş görevler için bir filtre vardır: `modified:recently`.

Bu sorgu, ayarlarda yapılandırılan pano vurgulama dönemiyle aynı değeri kullanır.

### Oluşturma Tarihine Göre Ara

Özellik: **created**

Değiştirme tarihi sorguları ile aynı şekilde çalışır.

### Başlangıç Tarihine Göre Ara

Özellik: **started**

### Açıklamaya Göre Ara

Özellik: **description** veya **desc**

Örnek: `description:"metin arama"`

### Dış Referansa Göre Ara

Görev referansı, görevinizin harici bir kimliği, örneğin başka bir yazılımdan gelen bir bilet numarasıdır.

- Görevleri referans ile bulun: `ref:1234` veya `reference:TICKET-1234`
- Joker arama: `ref:TICKET-*`

### Kategoriye Göre Ara

Özellik: **category**

- Belirli bir kategoriyle görevler: `category:"Feature Request"`
- Birden fazla kategoriyle görevler: `category:"Bug" category:"İyileştirmeler"`
- Kategorisi olmayan görevler: `category:none`

### Projeye Göre Ara

Özellik: **project**

- Proje adına göre görevler: `project:"Benim proje adım"`
- Proje kimliğine göre görevler: `project:23`
- Birden fazla projede görevler: `project:"Proje A" project:"Proje B"`

### Sütunlara Göre Ara

Özellik: **column**

- Sütun adına göre görevler: `column:"Devam eden işler"`
- Birden fazla sütunda görevler: `column:"Backlog" column:hazır`

### Kulvarlara Göre Ara

Özellik: **swimlane**

- Kulvarlara göre görevler: `swimlane:"Version 42"`
- Birden fazla kulvarda görevler: `swimlane:"Version 1.2" swimlane:"Version 1.3"`

### Görev Bağlantısına Göre Ara

Özellik: **link**

- Bağlantı adına göre görevler: `link:"is a milestone of"`
- Birden fazla bağlantıya göre görevler: `link:"is a milestone of" link:"relates to"`

### Yorumlara Göre Ara

Özellik: **comment**

- Belirli bir başlık içeren yorumlar: `comment:"Yorum mesajım"`

### Etiketlere Göre Ara

Özellik: **tag**

- Örnek: `tag:"Etiketim"`

Etkinlik Akışı Arama
--------------------

### Görev Başlıklarına Göre Etkinlik Arama

Özellik: **title** veya yok (varsayılan)

- Örnek: `title:"Benim Görevim"`
- Görev kimliğiyle: `#123`

### Görev Durumuna Göre Olayları Arama

Özellik: **status**

### Olay Yaratıcısına Göre Arama

Özellik: **creator**

### Olay Oluşturma Tarihine Göre Ara

Özellik: **created**

### Etkinlikleri Projeye Göre Ara

Özellik: **project**
