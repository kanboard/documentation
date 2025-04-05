---
title: Takvimlerinizi (eş zamanlı bilgi aktarma) senkronize etme
toc: true
menu:
    main:
        parent: Kullanici rehberi
---

Kanboard, projeler ve kullanıcılar için iCal özet akışlarını destekler.
Bu özellik, neredeyse tüm takvim programlarında (örneğin Microsoft Outlook, Apple Takvim, Mozilla Thunderbird ve Google Takvim) Kanboard görevlerini almanıza olanak tanır.

Takvim abonelikleri **yalnızca okunur** erişimindedir; dışarıdan kullandığınız takvim yazılımından görevler oluşturamazsınız.
Takvim beslemesi (feed) dışa aktarma, iCal standardını takip eder.

Not: Yalnızca -2 ay (önceki) ila +6 aylık (sonraki) tarih aralıklarındaki görevler iCalendar beslemesine aktarılır.

Proje Takvimleri
-----------------

- Her projenin kendi takvimi vardır.
- Proje başına abonelik bağlantısı benzersizdir. Projenizin herkese açık erişimini etkinleştirdiğinizde bu bağlantı etkinleştirilir: **Proje Ayarları > Herkese Açık Erişim**.
- Bu takvim, seçilen proje için yalnızca görevleri gösterir.

Kullanıcı Takvimleri
--------------------

- Her kullanıcının kendi takvimi vardır.
- Kullanıcı başına abonelik bağlantısı benzersizdir. Kullanıcının herkese açık erişimini etkinleştirdiğinizde bağlantı etkinleştirilir: **Kullanıcı Profili > Herkese Açık Erişim**.
- Bu takvim, kullanıcılara tüm projeler için atanan görevleri gösterir.

Kanboard Takviminizi Apple Takvim'e Eklemek
-------------------------------------------

- Takvim'i açın.
- **Dosya > Yeni Takvim Aboneliği** seçeneğini seçin.
- Kanboard'dan iCal özet akışı (feed) URL'sini kopyalayıp yapıştırın.

![iCal aboneliğini ekleyin](../screenshots/apple-calendar-add-subscription.png)

- Takvimi iCloud ile senkronize etmeyi seçerek tüm cihazlarınızda mevcut hale getirebilirsiniz.
- Yenileme sıklığını seçmeyi unutmayın.

![Edit iCal subscription](/images/v1/apple-calendar-edit-subscription.png)

Kanboard Takviminizi Microsoft Outlook'a Eklemek
------------------------------------------------

![Outlook Add Internet Calendar](/images/v1/outlook-add-subscription.png)

- Outlook'u açın.
- **Takvimi Aç > İnternet'ten** seçeneğini seçin.
- Kanboard'dan iCal özet akışı (feed) URL'sini kopyalayıp yapıştırın.

![Outlook Edit Internet Calendar](/images/v1/outlook-edit-subscription.png)

Kanboard Takviminizi Mozilla Thunderbird'e Eklemek
--------------------------------------------------

- Thunderbird'e takvim desteği eklemek için **Lightning** eklentisini yükleyin.
- **Dosya > Yeni Takvim** seçeneğine tıklayın.
- İletişim kutusunda **Ağda** seçeneğini belirleyin.

![Thunderbird Step 1](/images/v1/thunderbird-new-calendar-step1.png)

- iCalendar biçimini seçin.
- Kanboard'dan iCal özet akışı (feed) URL'sini kopyalayıp yapıştırın.

![Thunderbird Step 2](/images/v1/thunderbird-new-calendar-step2.png)

- Renkleri ve diğer ayarları seçin ve sonunda kaydedin.

Kanboard Takviminizi Google Takvim'e Eklemek
--------------------------------------------

- **Diğer Takvimler** yanındaki aşağı oku tıklayın.
- Menüden **URL Ekle** seçeneğini seçin.
- Kanboard'dan iCal özet akışı (feed) URL'sini kopyalayıp yapıştırın.

![Google Calendar](/images/v1/google-calendar-add-subscription.png)

Senkronizasyonu etkinleştirirseniz, Kanboard takviminiz Android cihazınızdan da kullanılabilir.

Not: Google Destek'e göre, harici takvimler çok sık yenilenmez. [Belgeleri okuyun](https://support.google.com/calendar/answer/37100?hl=en&ref_topic=1672445).
