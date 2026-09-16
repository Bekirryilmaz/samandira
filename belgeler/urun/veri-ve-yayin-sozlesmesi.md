# Veri ve Yayin Sozlesmesi

## 1. Belgenin Otoritesi

Bu belge, [urun-sozlesmesi.md](./urun-sozlesmesi.md) altındaki veri, kanıt ve yayın sözleşmesidir.

Ne tür bilginin karara girebileceğini, neyin public olamayacağını ve LLM'in kaynak olmadığını tanımlar. Uygunluk hesabı [domain-ve-karar-sozlesmesi.md](./domain-ve-karar-sozlesmesi.md) içindedir. Depolama ve request-time sınırı [sistem-sinirlari.md](./sistem-sinirlari.md) içindedir.

## 2. Temel Ilke

Ham veri gerçek değildir.

Bir kaydın, yorumun, etiketin veya model çıktısının varlığı; olgunun doğruluğunu, şube kimliğini, güncelliğini veya public kullanılma hakkını kanıtlamaz.

Bilginin doğruluğu ile onu public kullanma hakkı ayrı kapılardır. Biri diğerini açmaz.

## 3. Epistemik Turler

Kararda ve depoda şu türler karıştırılmaz:

| Tür | Anlam | Kararda tek başına yetmez çünkü |
| --- | --- | --- |
| `fact` | Sonradan doğrulanabilir, kapsamı belli olgu | Yoksa uydurulamaz; varsa da yayın hakkı ayrıca gerekir |
| `experience_signal` | Belirli ziyaret/bağlamda yaşanan deneyim | Fact değildir; hard PASS/FAIL üretmez |
| `generic_sentiment` | Genel beğeni veya tepki | Suitability değildir |
| `unknown` | Bu iddia için yeterli dayanak yok | `false` değildir |
| `stale` | Bir zaman doğruydu; şimdi taşınamaz | Güncel fact gibi kullanılamaz |
| `conflicting` | Çözülmemiş çelişki | Olumlu kabul edilemez |

Genel “güzel”, “kaliteli”, “en iyi” ifadeleri `generic_sentiment` olabilir. Uygunluk iddiasına çevrilmez.

## 4. Gozlem, Kanit ve Iddia Ayrimi

- **Gözlem:** Bir kaynağın, bir zamanda, bir yer adayı hakkında söylediği ham veya ayrıştırılmış kayıt.
- **Kanıt:** Kullanım hakkı, kimlik eşleşmesi ve kapsamı kontrol edilmiş dayanak.
- **İddia:** Belirli bir yer ve kapsam için kararda kullanılabilir hale gelmiş önerme.
- **Yayımlanmış iddia:** Public kapıdan geçmiş iddia.

Gözlem kanıt değildir. Kanıt iddia değildir. İddia yayımlanmış bilgi değildir. Zincirin bir halkası diğerini ima etmez.

## 5. Provenance

Her kullanılabilir kayıt şunları kaybedemez:

- kaynak
- hangi yer / şube adayı
- gözlem veya derleme zamanı
- çıkarım yöntemi varsa sürümü
- hak amacı (işleme, türev, saklama, public)

Kaynağı, yeri veya zamanı bilinmeyen girdi karara “sağlam” girmez. Model güveni provenance yerine geçmez.

## 6. Freshness

Değişebilen bilgi kalıcı gerçek gibi taşınmaz.

Saat, fiyat, yoğunluk, açık/kapalı ve benzeri iddialar aileye uygun geçerlilik taşır. Tarihi bilinmeyen kayıt güncel sayılmaz. `stale` sessizce `fact` olmaz.

## 7. Kaynak Politikasi

Kaynak seçimi hacme göre değil; hak, kimlik, doğrulanabilirlik ve bakıma göre yapılır.

- Resmi veya yapılandırılmış kaynak, ilgili fact için tercih edilir.
- Kullanım şartı ürün sınırlarıyla çelişiyorsa o kaynak ilgili çıktı için kullanılamaz.
- Bir amaçtaki izin (ör. dahili işleme) başka amaca (ör. public gösterim) taşınmaz.
- Scraper çoğaltmak, hak ve yayın darboğazını çözmez.

## 8. Google Yorumlari

Google yorumları internal offline NLP girdisi olabilir. Public ürün yüzeyi değildir.

Yasak:

- raw review public yayını
- reviewer identity public yayını
- sentiment yüzdesinin public skor olarak sunulması
- public review score
- `experience_signal`'ın fact sayılması
- `experience_signal`'dan hard PASS/FAIL üretilmesi
- request-time ağır yorum NLP'si

Yorum hacmi fact coverage değildir. Hak unknown iken türev iddia ve public claim üretilmez.

## 9. LLM ve AI Siniri

LLM source of truth değildir.

AI; metni ayrıştırmaya, aday üretmeye ve yetkili kararı anlaşılır anlatmaya yardım edebilir. AI:

- zorunlu koşulu gevşetmez
- kanıtsız iddiayı geçirmez
- bilinmeyen bilgiyi tamamlamaz
- ticari avantaj eklemez
- yeni gerekçe uydurmaz

Akıcı anlatım, kanıtı izlenemez hale getirirse kullanılmaz.

## 10. Publication

Publication ayrı kapıdır.

Dahilde bulunmak, public gösterilmeye yetmez. Otomatik yayın yoktur. Geri çekme, bağlı public çıktıların etkisini kaldırmak zorundadır. İndeks ve önbellek hakikatin sahibi değildir.

## 11. Public / Internal Siniri

Public yüzeye çıkmaz:

- ham yorum ve yeniden yazılmış yorum pasajı
- yorumcu kimliği
- dahili skor, model confidence, sentiment yüzdesi
- henüz yayımlanmamış gözlem, aday ve inceleme izi

Public yüzey yalnız yayımlanmış anlamı, gerekçeyi, ödünü ve karar açısından önemli bilinmeyeni taşır.

## 12. Veri Kalitesi Ilkeleri

- Kayıt sayısı olgunluk değildir.
- Aynı isimli şubeler ve belirsiz kimlikler birleştirilerek “daha çok kanıt” üretilmez.
- Tek kaynaklı tekrar, bağımsız kanıt sayılmaz.
- Amaç listesinde olmayan değer `known false` sayılmaz.
- Kalite eşiği uydurulmaz; etiket ve hak yoksa fail-closed kalınır.

## 13. Kaynak Degisikligi ve Yeniden Dogrulama

Kaynak, hak, çıkarım kuralı veya kimlik kuralı değişirse bağlı iddialar kendiliğinden geçerli kalmaz.

Yeniden doğrulama gerekir. Eski türev, yeni kaynağın fact'i gibi taşınmaz. Şüphede iddia daraltılır veya `unknown` olur; sessizce korunmaz.

## 14. Veri Invariantlari

- Ham observation fact değildir.
- `fact` / `experience_signal` / `generic_sentiment` ayrıdır.
- `unknown != false`
- Kritik unknown positive match dayanağı olamaz.
- Provenance ve freshness korunur.
- Publication ayrı kapıdır.
- LLM source of truth değildir; bilinmeyen bilgi uydurulmaz.
- Google raw review, reviewer identity ve sentiment yüzdesi public değildir.
- Sentiment yüzdesi public skor değildir.
- `experience_signal` hard PASS/FAIL üretmez.
