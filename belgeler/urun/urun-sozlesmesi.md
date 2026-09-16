# SAMANDIRA Urun Sozlesmesi

## 1. Belgenin Otoritesi

Bu belge SAMANDIRA'nın en üst ürün otoritesidir.

Alt belgeler bu sözleşmeyi uygulamak için vardır; sessizce değiştirmez:

- MVP sınırı: [mvp-kapsami.md](./mvp-kapsami.md)
- Karar kavramları: [domain-ve-karar-sozlesmesi.md](./domain-ve-karar-sozlesmesi.md)
- Veri ve yayın: [veri-ve-yayin-sozlesmesi.md](./veri-ve-yayin-sozlesmesi.md)
- Sistem sınırları: [sistem-sinirlari.md](./sistem-sinirlari.md)

Bu belgeye kesin coğrafya, kesin amaç listesi, endpoint, framework, veritabanı tablosu veya skor formülü yazılmaz.

## 2. Cozdugumuz Problem

Asıl problem yer listesi eksikliği değildir. Asıl problem, bulunan yerin **bu kişiye, bu gruba ve bu ana** uyup uymadığını anlayamamaktır.

Popülerlik, yıldız, yorum yığını ve “güzel görünme” bu yükü kaldırmaz. Kullanıcı araştırma yaptıkça her zaman daha iyi karar vermez; çoğu zaman yorulur.

SAMANDIRA, uygunluğu değerlendirme yükünü azaltmak için vardır.

## 3. Kimin Icin?

Dışarıda zaman geçirmek isteyen, ama “nereye gitsek?” sorusunda takılan insanlar içindir.

Hesap açmış uzman gezgin, içerik üreticisi veya işletme sahibi ilk kullanıcı tanımı değildir. İşletme ve operasyon ihtiyaçları bu sözleşmenin merkezini kaydırmaz.

## 4. Urun Vaadi

Kullanıcı şu üç soruya yeterli cevap bulabilmelidir:

- Bu yer şu an istediğim deneyime uygun mu?
- Seçersem hangi koşulu veya ödünü kabul ediyorum?
- Karar vermek için yeterince biliyor muyum?

Başarı, üründe geçirilen süre değil; verilen kararın gerçek hayatta karşılık bulmasıdır.

## 5. SAMANDIRA Nedir?

SAMANDIRA, bağlama göre az sayıda anlamlı seçenek üreten bir **karar ürünüdür**.

Çekirdek ilke:

> SAMANDIRA insanlara “en iyi” yeri göstermeye çalışmaz; kendileri için doğru olan yeri en kısa yoldan bulmalarını sağlar.

“Doğru yer” herkes için aynı değildir. Aynı insan için bile güne, bütçeye, yanındakilere ve o anki ihtiyaca göre değişir.

## 6. SAMANDIRA Ne Degildir?

SAMANDIRA şunlar değildir:

- gezi kataloğu
- review sitesi
- sosyal ağ
- marketplace
- sponsorlu sıralama ürünü
- LLM'in serbestçe yer uydurduğu sohbet botu

Harita, liste, içerik veya rota bir ihtiyaca hizmet edebilir. Bunların varlığı ürünün varlık nedenini değiştirmez.

## 7. Temel Deger

Kullanıcıya taşınan değer dört parçadan oluşur:

1. az sayıda anlamlı seçenek
2. neden
3. ödün
4. bilinmeyenler

Bu dördünden biri yoksa öneri tamamlanmış sayılmaz. Sayı doldurmak değer değildir.

## 8. Urun Ilkeleri

- **Uygunluk:** Genel itibar, belirli bir ihtiyaca uygunluk değildir.
- **Açıklık:** Öneri, neden tercih edilebileceğini ve ne zaman seçilmemesi gerektiğini taşır.
- **Dürüstlük:** Bilinen, yorumlanan ve bilinmeyen karıştırılmaz. Kesin görünerek değil, beklentiyi doğru kurarak güven kazanılır.
- **Özerklik:** Ürün karar vermeyi kolaylaştırır; kullanıcı adına neyi sevmesi gerektiğine karar vermez.
- **Gerçek hayat değeri:** Kullanıcıyı üründe tutmak başarı değildir. Kararını verip ayrılabilmesi başarıdır.

İlkeler çatıştığında: dürüstlük hızdan, açık ihtiyaç varsayımdan, güven ticari kazançtan önce gelir.

## 9. Degismez Urun Invariantlari

- “En iyi yer” ilan edilmez.
- Ticari ilişki uygunluk gibi sunulmaz; organic karar satın alınamaz.
- Bilinen önemli dezavantaj, seçimi teşvik etmek için saklanmaz.
- Yeterli dayanak yokken kesinlik üretilmez; bilinmeyen bilgi uydurulmaz.
- Zayıf adayla boşluk doldurulmaz. “Uygun seçenek bulamadık” geçerli sonuçtur.
- Kullanıcı zevki, bütçesi veya tercihi nedeniyle yargılanmaz.
- Popülerlik, fiyat veya gösteriş kendiliğinden kalite kabul edilmez.

Karar, veri ve sistem ayrıntıları alt canonical belgelerdedir. Bu maddeler onların üst sınırıdır.

## 10. Kapsam Degisikligi Kurali

Bu sözleşmedeki vaat, “ne değildir” listesi ve invariantlar sessizce daraltılamaz veya genişletilemez.

Kapsam değişimi:

1. hangi kullanıcı ihtiyacının değiştiğini yazar
2. hangi invariantın etkilediğini belirtir
3. [mvp-kapsami.md](./mvp-kapsami.md) veya ilgili alt belgeyi günceller
4. gerekirse `belgeler/kararlar/` altında kayıt açar

Kod, tasarım veya teknik fırsat tek başına bu belgeyi değiştirmez.
