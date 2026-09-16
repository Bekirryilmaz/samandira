# Domain ve Karar Sozlesmesi

## 1. Belgenin Otoritesi

Bu belge, [urun-sozlesmesi.md](./urun-sozlesmesi.md) altındaki karar domain sözleşmesidir.

Uygunluğun nasıl kurulacağını, hangi yeteneğin hangi işi yaptığını ve frontend'in karar üretmeyeceğini tanımlar. MVP'ye girip girmeme [mvp-kapsami.md](./mvp-kapsami.md) içindedir. Kanıt türleri ve yayın [veri-ve-yayin-sozlesmesi.md](./veri-ve-yayin-sozlesmesi.md) içindedir.

## 2. Temel Domain Kavramlari

- **Yer:** Belirli bir fiziksel kimlik. Şube, taşınmış işletme ve salon/teras aynı kayıt gibi birleştirilmez.
- **Amaç:** Kullanıcının bu ziyarette yapmak istediği şey. Yer türü amaç değildir.
- **Zorunlu koşul (hard constraint):** Karşılanmazsa aday bu bağlamın uyumlu seçeneklerinden çıkar.
- **Tercih (soft preference):** Sıralamada anlam üretir; zorunlu koşulu ezmez.
- **Ziyaret bağlamı:** Zaman, bütçe, grup, ulaşım ve benzeri bu ana ait koşullar.
- **Uygunluk:** Yer + amaç + koşullar + bağlam + kullanılabilir dayanak ilişkisidir. Yere yapıştırılmış kalıcı puan değildir.
- **Aday:** Search'in getirdiği yer. Aday olmak uygun olmak değildir.
- **Seçenek:** Karar Motorunun gerekçe, ödün ve bilinmeyenle ürettiği sonuç.

## 3. Arama

Arama aday bulur.

İsim, coğrafya, tür ve benzeri erişim sinyalleriyle yeterli havuz kurar. Uygunluk, gerekçe, ödün veya sıralama otoritesi değildir. Popüler veya çok verili yerleri taramak aramanın başarı ölçüsü değildir.

Bir yerin adını arayan kullanıcıya kayıt gösterilebilir. Bu, o yerin koşullarına uygun önerildiği anlamına gelmez.

## 4. Kesfet

Keşfet, Search + Karar Motoru kullanan karar akışıdır.

Ayrı recommendation engine değildir. Keşfet; bağlamı alır, aday ister, Karar Motoruna sorar, az sayıda anlamlı seçeneği taşır. Sayı kotası için zayıf aday eklemez. Anlamlı fark yoksa daha az sonuç üretir veya dürüstçe boş döner.

## 5. Karar Motoru

Karar Motoru tek suitability authority'dir.

İşi, kullanılabilir bilgiyi bu ziyaretin ihtiyacıyla ilişkilendirip gerekçeli seçim alanı üretmektir. Her soruya bir yer söylemek başarı değildir.

Sıra:

1. Ziyaretin gerçekleşmesini ve hard constraint'leri denetle
2. Ana amacı değerlendir
3. Soft preference ve ödünleri karşılaştır
4. Kararı değiştirecek bilinmeyenleri görünür tut
5. Az sayıda, birbirinin kopyası olmayan seçenek bırak

Tek toplam puan organik kararı taşımaz. Engel ve unknown, ortalamada eritilmez.

## 6. Unknown Davranisi

`unknown != false`. Bilinmeyen, yok veya uymuyor demek değildir.

- Kritik unknown, positive match değildir. Hard constraint karşılanmış sayılmaz.
- Soft preference unknown'u adayı otomatik elemez; ama “destekleniyor” da denmez.
- Çelişen kanıt, olumlu kabul edilmez.
- Eksik bilgi kullanıcıya gizlenmez; karar açısından önemliyse seçeneğin yanında durur.

## 7. Bugun Ne Yapalim

Bugün Ne Yapalım, kullanıcının düşük eforlu girdisini yapılandırılmış karar bağlamına dönüştürür.

Ayrı motor değildir. Niyet anlama, Search ve Karar Motorunun önündeki giriş kapısıdır. Anlaşılmayan koşulu silmez, kullanıcı adına zorunlu koşul uydurmaz. Netleştirme, adayları veya kritik bir koşulu değiştirecekse sorulur; uzun anket yoktur.

## 8. Gunluk Akilli Rota

Günlük Akıllı Rota, Karar Motorundan geçmiş yerleri zaman ve hareket problemi olarak planlar.

Suitability'yi yeniden hesaplamaz. Route Engine suitability authority değildir. Durak uygunluğu Karar Motorunun sonucudur; rota yalnızca sıra, süre, geçiş ve toplam yükü düzenler.

Planlama çıktısı tahmindir. Estimate fact gibi sunulmaz. Savunulabilir dizi yoksa sonuç üretilmez. Tek yer ana amacı karşılıyorsa tek yer yeterlidir.

## 9. Akilli Gezi

Akıllı Gezi, çok günlük ayrı ürün genişlemesidir. MVP dışıdır.

Günlük Akıllı Rota'nın gün sayısını artırmak Akıllı Gezi üretmez. Konaklama organizasyonu, şehirler arası seyahat yönetimi ve çok günlük takvim bu sözleşmenin günlük kararının parçası değildir.

## 10. Ticari Tarafsizlik

Sponsor, ortaklık, ödeme veya envanter ilişkisi:

- organic uygunluğu değiştirmez
- organic sıralamayı değiştirmez
- hard constraint veya unknown kapısını açmaz

Ticari bildirim ayrı alandır. Görünürlük satın almak, karar satın almak değildir.

## 11. Frontend Karar Yasagi

Frontend uygunluk hesaplamaz.

Kart yüksekliği, fotoğraf, sponsor işareti, Premium durumu veya yerel sıralama, Karar Motorunun sırasını değiştirmez. Frontend; yetkili sonucu gösterir, kullanıcı girdisini taşır, boş/hata/unknown durumlarını dürüstçe sunar.

## 12. Domain Invariantlari

- Search aday bulur; Keşfet ayrı recommendation engine değildir.
- Tek Karar Motoru vardır.
- Frontend uygunluk hesaplamaz.
- `unknown != false`
- Kritik unknown positive match değildir.
- Hard constraint puanla telafi edilemez.
- Soft preference unknown adayı otomatik elemez ve “destekleniyor” iddiası kurmaz.
- Zayıf adaylarla sayı doldurulmaz.
- Sponsor organic uygunluğu veya sıralamayı etkilemez.
- Günlük Akıllı Rota != Akıllı Gezi
- Route Engine suitability authority değildir.
- Estimate fact gibi sunulmaz.
