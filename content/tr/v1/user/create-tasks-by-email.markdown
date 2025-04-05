---
title: E-posta ile Görevler Oluşturma
toc: true
menu:
    main:
        parent: Kullanici rehberi
---

Bir e-posta göndererek görevleri doğrudan oluşturabilirsiniz.
Bu özellik eklentiler kullanılarak sağlanır.

Şu anda Kanboard, 3 harici hizmetle entegre edilmiştir:

- [Mailgun](https://github.com/kanboard/plugin-mailgun)
- [Sendgrid](https://github.com/kanboard/plugin-sendgrid)
- [Postmark](https://github.com/kanboard/plugin-postmark)

Bu hizmetler, herhangi bir SMTP sunucusunu yapılandırmak zorunda kalmadan gelen e-postaları işler.

Bir e-posta alındığında, Kanboard belirli bir son noktadaki mesajı alır.
Tüm karmaşık işlemler bu hizmetler tarafından gerçekleştirilir.

Gelen E-postaların İş Akışı
---------------------------

1. Belirli bir adrese bir e-posta gönderirsiniz, örneğin **something+myproject@inbound.mydomain.tld**.
2. E-postanız, üçüncü parti SMTP sunucularına yönlendirilir.
3. SMTP sağlayıcısı, Kanboard web kancasını (hook) çağırarak e-postayı JSON veya çok parçalı/form-veri formatında gönderir.
4. Kanboard, alınan e-postayı ayrıştırır ve doğru projeye göre bir görev oluşturur.

Not: Yeni görevler otomatik olarak ilk sütunda oluşturulur.

E-posta Biçimi
--------------

- E-posta adresinin yerel kısmı artı ayırıcıyı kullanmalıdır, örneğin **kanboard+project123**.
- Artı işaretinden sonra tanımlanan dize, bir proje tanımlayıcısıyla eşleşmelidir, örneğin **project123** projenin tanımlayıcısıdır.
- E-posta konusu görev başlığı haline gelir.
- E-posta gövdesi görev açıklaması olur (Markdown biçimi).

Gelen e-postalar metin veya HTML biçiminde olabilir.
**Kanboard, basit HTML e-postalarını Markdown** biçimine dönüştürebilir.

Güvenlik ve Gereksinimler
-------------------------

- Kanboard web kancası rastgele bir token ile korunur.
- Gönderenin e-posta adresi bir Kanboard kullanıcısıyla eşleşmelidir.
- Kanboard projesinin benzersiz bir tanımlayıcısı olmalıdır, örneğin **PROJEM**.
- Kanboard kullanıcısının projeye üye olması gerekir.
