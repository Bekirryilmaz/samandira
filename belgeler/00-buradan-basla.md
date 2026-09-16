# Buradan Basla

## 1. Bu Belgenin Amaci

Bu dosya ürün kaynağı değildir. Belge haritasıdır.

Hangi sorunun hangi canonical belgede yanıtlandığını gösterir. Ürün davranışı, kapsam, domain kuralı veya veri politikası buradan türetilmez.

## 2. Canonical Otorite

En üst ürün otoritesi:

- [urun/urun-sozlesmesi.md](urun/urun-sozlesmesi.md)

Alt canonical belgeler, kendi sahiplik alanında bağlayıcıdır:

- [urun/mvp-kapsami.md](urun/mvp-kapsami.md) — MVP sınırı
- [urun/domain-ve-karar-sozlesmesi.md](urun/domain-ve-karar-sozlesmesi.md) — karar kavramları
- [urun/veri-ve-yayin-sozlesmesi.md](urun/veri-ve-yayin-sozlesmesi.md) — veri ve yayın
- [urun/sistem-sinirlari.md](urun/sistem-sinirlari.md) — sistem sorumlulukları

Canonical olmayan belgeler:

- [../README.md](../README.md)
- [../AGENTS.md](../AGENTS.md)
- bu dosya
- [legacy/eski-projeden-dersler.md](legacy/eski-projeden-dersler.md)

Çelişkide canonical ürün belgeleri kazanır. Aynı bilgi iki canonical belgede ayrıntılı tekrar edilmez; sahiplik tablodaki belgeye aittir.

## 3. Hangi Soruda Hangi Belge?

| Soru | Belge |
| --- | --- |
| SAMANDIRA nedir, ne değildir, kimin için? | [urun/urun-sozlesmesi.md](urun/urun-sozlesmesi.md) |
| Ürün vaadi ve değişmez ürün ilkeleri nedir? | [urun/urun-sozlesmesi.md](urun/urun-sozlesmesi.md) |
| MVP neyi doğrular, neler dışarıdadır? | [urun/mvp-kapsami.md](urun/mvp-kapsami.md) |
| Coğrafya veya amaç resmi olarak kilitlendi mi? | [urun/mvp-kapsami.md](urun/mvp-kapsami.md) |
| Arama, Keşfet ve Karar Motoru nasıl ayrılır? | [urun/domain-ve-karar-sozlesmesi.md](urun/domain-ve-karar-sozlesmesi.md) |
| Unknown, hard constraint, soft preference nasıl davranır? | [urun/domain-ve-karar-sozlesmesi.md](urun/domain-ve-karar-sozlesmesi.md) |
| Bugün Ne Yapalım, Günlük Akıllı Rota, Akıllı Gezi nedir? | [urun/domain-ve-karar-sozlesmesi.md](urun/domain-ve-karar-sozlesmesi.md) |
| Frontend uygunluk hesaplayabilir mi? | [urun/domain-ve-karar-sozlesmesi.md](urun/domain-ve-karar-sozlesmesi.md) |
| Fact, experience_signal, sentiment nasıl ayrılır? | [urun/veri-ve-yayin-sozlesmesi.md](urun/veri-ve-yayin-sozlesmesi.md) |
| Google yorumları public olur mu? | [urun/veri-ve-yayin-sozlesmesi.md](urun/veri-ve-yayin-sozlesmesi.md) |
| LLM kaynak kabul edilir mi? | [urun/veri-ve-yayin-sozlesmesi.md](urun/veri-ve-yayin-sozlesmesi.md) |
| Bilgi doğru olsa da public kullanılabilir mi? | [urun/veri-ve-yayin-sozlesmesi.md](urun/veri-ve-yayin-sozlesmesi.md) |
| Frontend / backend / API sınırı nedir? | [urun/sistem-sinirlari.md](urun/sistem-sinirlari.md) |
| Request-time NLP yapılır mı? | [urun/sistem-sinirlari.md](urun/sistem-sinirlari.md) |
| Başlangıç teknik yönü nedir? | [urun/sistem-sinirlari.md](urun/sistem-sinirlari.md) |
| Ajan nasıl çalışır, commit/push kuralı nedir? | [../AGENTS.md](../AGENTS.md) |
| Eski projeden hangi ders alındı? | [legacy/eski-projeden-dersler.md](legacy/eski-projeden-dersler.md) |
| Bu kararı kim, neden verdi? | `belgeler/kararlar/` (henüz yok; §5) |

## 4. Onerilen Okuma Sirasi

1. Bu harita
2. [urun/urun-sozlesmesi.md](urun/urun-sozlesmesi.md)
3. [urun/mvp-kapsami.md](urun/mvp-kapsami.md)
4. [urun/domain-ve-karar-sozlesmesi.md](urun/domain-ve-karar-sozlesmesi.md)
5. [urun/veri-ve-yayin-sozlesmesi.md](urun/veri-ve-yayin-sozlesmesi.md)
6. [urun/sistem-sinirlari.md](urun/sistem-sinirlari.md)
7. Gerekirse [legacy/eski-projeden-dersler.md](legacy/eski-projeden-dersler.md)
8. Operasyon için [../AGENTS.md](../AGENTS.md)

## 5. Karar Belgeleri

Gelecekte gerekçeli kapsam, kural veya teknik yön değişiklikleri şu yolda tutulur:

`belgeler/kararlar/K-XXXX-kisa-karar-adi.md`

Bu klasör şimdi boş olarak açılmaz. Git boş klasörü takip etmez; `.gitkeep` de istenmez. Klasör, ilk gerçek karar kaydı yazıldığında oluşturulur.

Karar kaydı, ilgili canonical belgeyi sessizce ezmez. Canonical metin, karar kaydına atıfla güncellenir.

## 6. Legacy Belgeler

[legacy/eski-projeden-dersler.md](legacy/eski-projeden-dersler.md) tarihsel uyarıdır. Yeni ürün kuralı üretmez. Legacy repo içindeki belgeler ve kod, bu clean build'in parçası değildir.

## 7. Belge Degisikligi Kurali

- Canonical bilgi tek sahibinde durur.
- README ve AGENTS, canonical içeriği kopyalayarak ikinci kaynak olmaz.
- Ürün, kapsam, domain, veri veya mimari kuralı değişecekse önce ilgili canonical belge ve gerekirse karar kaydı güncellenir; sonra kod.
- Henüz kilitlenmemiş hipotez, kesin destek gibi yazılmaz.
