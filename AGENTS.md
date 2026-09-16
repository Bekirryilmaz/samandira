# SAMANDIRA Agent Kurallari

Bu dosya ürün spesifikasyonu değildir. Operasyonel çalışma kuralıdır. Ürün gerçeği [belgeler/urun/urun-sozlesmesi.md](belgeler/urun/urun-sozlesmesi.md) ve alt canonical belgelerdedir. Belge haritası: [belgeler/00-buradan-basla.md](belgeler/00-buradan-basla.md)

## 1. Repository Gercegi

- Aktif repo (`Bekirryilmaz/samandira`) tek kod ve belge gerçeğidir.
- Legacy repo (`Bekirryilmaz/gezi_bot`) salt-okunur referanstır.
- Legacy içinde dosya değiştirme, silme, commit, push, migration, formatlama veya refactor yapılmaz.
- Legacy implementasyonu kopyalanmaz. Ders alınır; kod taşınmaz.

## 2. Belge Otoritesi

En üst ürün otoritesi: [belgeler/urun/urun-sozlesmesi.md](belgeler/urun/urun-sozlesmesi.md)

Alt canonical belgeler:

- [belgeler/urun/mvp-kapsami.md](belgeler/urun/mvp-kapsami.md)
- [belgeler/urun/domain-ve-karar-sozlesmesi.md](belgeler/urun/domain-ve-karar-sozlesmesi.md)
- [belgeler/urun/veri-ve-yayin-sozlesmesi.md](belgeler/urun/veri-ve-yayin-sozlesmesi.md)
- [belgeler/urun/sistem-sinirlari.md](belgeler/urun/sistem-sinirlari.md)

`README.md`, bu dosya, [belgeler/00-buradan-basla.md](belgeler/00-buradan-basla.md) ve [belgeler/legacy/eski-projeden-dersler.md](belgeler/legacy/eski-projeden-dersler.md) canonical değildir. Çelişkide canonical ürün belgeleri kazanır.

## 3. Isimlendirme

Bizim belirlediğimiz klasör, belge, domain, kaynak ve modül adları Türkçe olur; dosya ve klasör adlarında Türkçe karakter kullanılmaz. Standart araç dosyaları (`README.md`, `AGENTS.md`, `.gitignore`, `package.json`, `pyproject.toml` vb.) istisnadır.

Klasörler gerçek içerik ihtiyacı doğmadan açılmaz. Boş klasör ve `.gitkeep` kullanılmaz.

## 4. Calisma Sirasi

1. Kullanıcı ihtiyacı
2. Ürün davranışı
3. Gerekli veri
4. Veri kaynağı
5. Domain sözleşmesi
6. Backend / API
7. Test
8. Frontend

İhtiyaç netleşmeden kod yazılmaz. Veri ve kaynak netleşmeden yetenek kilitlenmez. Testi olmayan karar kuralı frontend'e inmez.

## 5. Urun Invariantlari

Ayrıntı [belgeler/urun/domain-ve-karar-sozlesmesi.md](belgeler/urun/domain-ve-karar-sozlesmesi.md) içindedir. İhlal edilmez:

- Search aday bulur; uygunluk kararı vermez.
- Tek Karar Motoru vardır.
- Frontend uygunluk hesaplamaz.
- Zayıf adaylarla sayı doldurulmaz.
- Sponsor organic uygunluğu veya sıralamayı etkilemez.
- Günlük Akıllı Rota, Akıllı Gezi değildir.
- Route Engine suitability authority değildir.
- Estimate fact gibi sunulmaz.

## 6. Veri ve Epistemik Invariantlar

Ayrıntı [belgeler/urun/veri-ve-yayin-sozlesmesi.md](belgeler/urun/veri-ve-yayin-sozlesmesi.md) içindedir. İhlal edilmez:

- `unknown != false`
- Kritik unknown positive match değildir.
- Hard constraint puanla telafi edilemez.
- `fact`, `experience_signal` ve `generic_sentiment` ayrıdır.
- Ham observation fact değildir.
- LLM source of truth değildir.
- Bilinmeyen bilgi uydurulmaz.
- Provenance ve freshness korunur.
- Publication ayrı kapıdır.
- Google yorumları internal offline NLP girdisidir.
- Raw review public değildir.
- Reviewer identity public değildir.
- Sentiment yüzdesi public skor değildir.

## 7. Mimari Sinirlar

Ayrıntı [belgeler/urun/sistem-sinirlari.md](belgeler/urun/sistem-sinirlari.md) içindedir.

- Request-time ağır NLP yoktur.
- İhtiyaç olmadan microservice, Redis, Kafka, Elastic veya vector DB eklenmez.
- `web/`, `sunucu/`, `veri_hatti/`, `testler/`, `altyapi/` yalnız gerçek içerik ihtiyacında açılır.

## 8. Test ve Dogrulama

- Invariant testleri pazarlık konusu değildir.
- UI doğrulaması tek ekran görüntüsü değildir; ilgili akış uçtan uca işletilir.
- “Çalışıyor görünüyor” kanıt sayılmaz. Davranış, sözleşme ve yasak yüzeyler ayrı doğrulanır.

## 9. Git Guvenligi

Kullanıcı açıkça istemeden:

- commit yok
- push yok

Hook atlanmaz. Force push, hard reset ve benzeri yıkıcı git işlemleri açık istek olmadan yapılmaz.

## 10. Veri Guvenligi

- Production data açık izin olmadan değişmez.
- `.env` ve sırlar commit edilmez.
- Runtime/private veri `/veri/`, `/cikti/`, `/cache/` altındadır; bunlara ürün kodu konmaz.

## 11. Destructive Islemler

Silme, overwrite, migration, schema drop, toplu veri düzeltme ve benzeri yıkıcı işlemler:

- kapsamı yazılıdır
- geri alınabilirliği açıktır
- kullanıcı onayı vardır

Onay yoksa durulur.

## 12. Proje Yonetimi

- Canonical belgeyi sessizce değiştirme. Kapsam veya kural değişimi karar kaydı ister.
- Gelecekteki karar kayıtları `belgeler/kararlar/K-XXXX-kisa-karar-adi.md` biçimindedir. Bu klasör ilk gerçek kayıtta açılır.
- Mega görevle momentum üretilmez. Ürün, veri ve domain netleşmeden framework kurulmaz.
