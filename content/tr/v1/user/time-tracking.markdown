---
title: Zaman İzleme
toc: true
menu:
    main:
        parent: Kullanici rehberi
---

Zaman izleme bilgileri, görev seviyesinde veya alt görev seviyesinde tanımlanabilir.

Görev Zaman İzleme
------------------

![Task time tracking](/images/v1/task-time-tracking.png)

Görevlerin iki alanı vardır:

- Tahmini zaman
- Harcanan zaman

Bu değerler çalışma saatlerini temsil eder ve manuel olarak ayarlanmalıdır.

Alt Görev Zaman İzleme
----------------------

![Subtask time tracking](/images/v1/subtask-time-tracking.png)

Alt görevlerin "geçen süre" ve "zaman tahmini" alanları da vardır.

Bu alanların değerini değiştirdiğinizde, **görev zaman izleme değerleri otomatik olarak güncellenir ve tüm alt görev değerlerinin toplamı haline gelir**.

Kanboard, her bir alt görev durumu değişikliği arasındaki zamanı ayrı bir tabloda kaydeder:

- Alt görev durumu **yapılacak**tan **devam eden**e değiştirildiğinde başlangıç zamanı kaydedilir.
- Alt görev durumu **devam eden**den **tamamlanmış**a değiştirildiğinde bitiş zamanı kaydedilir ve alt görevin yanı sıra görevin geçen süresi de güncellenir.

Tüm kayıtların dökümü görev görünümü sayfasında görünür:

![Task timesheet](/images/v1/task-timesheet.png)

Her bir alt görev için zamanlayıcı istediğiniz zaman durdurulabilir veya başlatılabilir:

![Subtask timer](/images/v1/subtask-timer.png)

- Zamanlayıcı, alt görev durumuna bağlı değildir.
- Zamanlayıcıyı her başlattığınızda zaman takibi tablosunda yeni bir kayıt oluşturulur.
- Zamanlayıcıyı durdurduğunuzda bitiş tarihi saat izleme tablosuna kaydedilir.
- Hesaplanan geçen süre en yakın çeyreğe yuvarlanır (yalnızca Kanboard < 1.0.32 için).
