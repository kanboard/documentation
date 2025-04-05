---
title: Otomatik İşlemler
toc: true
menu:
    main:
        parent: Kullanici rehberi
---

Kullanıcı etkileşimini en aza indirgemek için, Kanboard otomatik işlemleri destekler.

Her otomatik işlem şu şekilde tanımlanır:

- Dinlemek için bir etkinlik.
- Bu etkinlikle bağlantılı işlem.
- Sonunda tanımlamak için bazı parametreler.

Her projenin farklı otomatik eylemler kümesi vardır. Proje giriş sayfasında yapılandırma panelinde bulunur, **Otomatik İşlemler** bağlantısına tıklayın.

Yeni Bir Eylem Ekle
-------------------

**Yeni bir otomatik işlem ekle** bağlantısını tıklayın.

![Automatique action](/images/v1/automatic-action-creation.png)

- Bir eylem seçin.
- Sonra bir etkinlik seçin.
- Ve son olarak, parametreleri tanımlayın.

Kullanılabilir İşlemlerin Listesi
---------------------------------

- Harici bir sağlayıcının yorumunu oluşturma.
- Görevi sütunlar arasında taşırken yorum günlüğü ekleme.
- Otomatik olarak bir renge dayalı bir kategori atama.
- Kategoriyi harici bir etikete göre değiştirin.
- Bağlantıya dayalı otomatik olarak bir kategori atama.
- Bir kategoriye dayalı otomatik olarak bir renk atama.
- Görev belirli bir kolona taşındığında renk atama.
- Belirli bir görev bağlantısı kullanırken görev rengini değiştirme.
- Belirli bir kullanıcıya renk atama.
- Görevi eylemi yapan kişiye atayın.
- Görevi, sütun değiştiğinde işlemi yapan kişiye atayın.
- Görevi belirli bir kullanıcıya atayın.
- Atanan kişiyi harici bir kullanıcı adına göre değiştirin.
- Görevi kapat.
- Görevi belirli bir sütunda kapatma.
- Harici bir sağlayıcıdan bir görev oluşturma.
- Görevin başka bir projeye kopyalanması.
- Görevi e-postayla birine gönderin.
- Görevi başka bir projeye taşıyın.
- Görevi bir kullanıcıya atandığında başka bir kolona taşıyın.
- Kategori değiştirildiğinde görevi başka bir kolona taşıyın.
- Görev sahibi silindiğinde, görevi başka bir kolona taşıyın.
- Görev aç.
- Başlangıç ​​tarihini otomatik olarak güncelleyin.

Örnekler
--------

### Bir Görevi "Bitti" Kolonuna Taşıdığımda, Bu Görevi Otomatik Olarak Kapat

- İşlemi seçin: **Bir görevi belirli bir sütunda kapatın**.
- Etkinliği seçin: **Görevi başka bir kolona taşıyın**.
- Eylem parametresini tanımlayın: **Kolon=Bitti** (hedef kolon budur).

### Bir Görevi "Doğrulanacak" Kolonuna Taşıdığımda, Bu Görevi Belirli Bir Kullanıcıya Atayın

- İşlemi seçin: **Görevi belirli bir kullanıcıya atayın**.
- Etkinliği seçin: **Görevi başka bir kolona taşıyın**.
- Eylem parametrelerini tanımlayın: **Kolon=Doğrulanacak** ve **Kullanıcı=Bob** (Bob bizim test görevlimizdir).

### Görevi "Çalışma Sürüyor" Kolonuna Taşıdığımda, Bu Görevi Geçerli Kullanıcıya Atayın

- İşlemi seçin: **Görevi, kolon değiştiğinde işlemi yapan kişiye atayın**.
- Etkinliği seçin: **Görevi başka bir kolona taşıyın**.
- Eylem parametresini tanımlayın: **Kolon=Çalışma Sürüyor**.

### Bir Görev Tamamlandığında, Bu Görevi Başka Bir Projeye Kopyalayın

Diyelim ki "Müşteri Siparişi" ve "Üretim" olmak üzere iki projemiz var. Sipariş onaylandıktan sonra onu "Üretim" projesine değiştirelim.

- İşlemi seçin: **Görevi başka bir projeye çoğaltın**.
- Etkinliği seçin: **Görevi kapatma**.
- Eylem parametrelerini tanımlayın: **Kolon=Doğrulanmış** ve **Proje=Üretim**.

### Bir Görev Son Kolona Taşındığında, Aynı Görevi Başka Bir Projeye Taşıyın

Diyelim ki iki proje "Fikirler" ve "Geliştirme" var. Bir kez fikir geçerliliği onaylandıktan sonra onu "Geliştirme" projesine taşıyalım.

- İşlemi seçin: **Görevi başka bir projeye taşıyın**.
- Etkinliği seçin: **Görevi başka bir kolona taşıyın**.
- Eylem parametrelerini tanımlayın: **Kolon=Doğrulanmış** ve **Proje=Geliştirme**.

### Bob Kullanıcısına Otomatik Olarak Bir Renk Atamak İstiyorum

- İşlemi seçin: **Belirli bir kullanıcıya renk atayın**.
- Etkinliği seçin: **Görev atayanı değiştir**.
- Eylem parametrelerini tanımlayın: **Renk=Yeşil** ve **Atayan=Bob**.

### Tanımlanan "Özellik İsteği" Kategorisine Otomatik Olarak Bir Renk Atamak İstiyorum

- İşlemi seçin: **Otomatik olarak bir kategoriye dayalı bir renk atayın**.
- Etkinliği seçin: **Görev oluşturma veya değiştirme**.
- Eylem parametrelerini tanımlayın: **Renk=Mavi** ve **Kategori=Özellik İsteği**.

### Görev "Çalışma Sürüyor" Sütununa Taşındığında Başlangıç ​​Tarihini Otomatik Olarak Ayarlamak İstiyorum

- İşlemi seçin: **Başlangıç ​​tarihini otomatik olarak güncelleyin**.
- Etkinliği seçin: **Görevi başka bir kolona taşıyın**.
- Eylem parametrelerini tanımlayın: **Kolon=Çalışma Sürüyor**.
