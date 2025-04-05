---
title: Çift-Kademeli Kimlik Doğrulama
toc: true
menu:
    main:
        parent: Kullanici rehberi
---

Her kullanıcı [Çift-Kademeli Kimlik Doğrulama (two-factor authentication)](http://en.wikipedia.org/wiki/Two_factor_authentication)'yı aktif edebilir.
Başarılı bir oturum açtıktan sonra, kullanıcıdan Kanboard'a erişim izni vermeleri için bir kerelik kod (6 karakter) istenecektir.

Bu kod, genellikle akıllı telefonunuza yüklü olan uyumlu bir yazılım tarafından sağlanmalıdır.

Kanboard, [RFC 6238](http://tools.ietf.org/html/rfc6238) içinde tanımlanan [Zamana Dayalı Bir Kerelik Şifre Algoritması (Time-based One-time Password Algorithm)](http://en.wikipedia.org/wiki/Time-based_One-time_Password_Algorithm)'nı kullanır.

Standart TOTP sistemi ile uyumlu birçok yazılım bulunmaktadır.
Örneğin, şu uygulamaları kullanabilirsiniz:

- [Google Authenticator](https://github.com/google/google-authenticator/) (Android, iOS, Blackberry)
- [FreeOTP](https://freeotp.github.io/) (Android, iOS)
- [OATH Toolkit Araç Seti](http://www.nongnu.org/oath-toolkit/) (Unix/Linux'da komut satırı yardımcı programı)

Bu sistem çevrimdışı çalışabilir ve mutlaka cep telefonunuz olması gerekmez.

Kurulum
-------

1. Kullanıcı profilinize gidin.
2. Sol tarafta **İki faktörlü kimlik doğrulama** seçeneğini tıklayın ve kutuyu işaretleyin.
3. Sizin için gizli bir anahtar oluşturulur.

![2FA](/images/v1/2fa.png)

- TOTP yazılımında gizli anahtarı kaydetmeniz gerekir. Akıllı telefon kullanıyorsanız, en kolay çözüm QR kodunu FreeOTP veya Google Authenticator ile taramaktır.
- Her sefer yeni bir oturum açtığınızda, yeni bir kod sorulur.
- Oturumunuzu kapatmadan önce cihazınızı test etmeyi unutmayın.

Bu özelliği her etkinleştirdiğinizde veya devre dışı bıraktığınızda yeni bir gizli anahtar oluşturulur.
