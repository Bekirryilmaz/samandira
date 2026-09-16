# Eski Projeden Dersler

## 1. Belgenin Amaci ve Siniri

Bu belge canonical değildir. Legacy `gezi_bot` deneyiminden çıkarılmış uyarılardır.

Yeni sistemin parçasını tarif etmez. Legacy kod, şema, skor, ekran veya migration yeni ürünün temeli sayılmaz. Çelişkide [../urun/urun-sozlesmesi.md](../urun/urun-sozlesmesi.md) ve alt canonical belgeler kazanır.

Her ders üç parçadır: **GOZLEM**, **SONUC**, **CLEAN BUILD DERSI**.

## 2. Fazla Veri vs Kaliteli Veri

**GOZLEM:** Legacy Samsun katalogunda 1719 yer vardı. Karar ailelerinin çoğunda known fact hemen hemen sıfırdı; amaç desteği yalnızca bir avuç yerde görünüyordu.

**SONUC:** 1719 yer, kaliteli karar demek değildi. Hacim, “şehir hazır” iddiasını taşıyamaz.

**CLEAN BUILD DERSI:** Olgunluk kayıt sayısıyla ölçülmez. Bir yer, ilgili iddia yayımlanabilir olmadan hazır aday sayılmaz.

## 3. Veri Kaynagi Secimi

**GOZLEM:** Çok kaynaklı toplama (OSM, Google, diğer denemeler) katalog büyüttü. Hak, kimlik ve freshness aynı hızda büyümedi. 19.609 Google yorumu fact coverage üretmedi.

**SONUC:** Kaynak çeşitliliği, kullanılabilir bilgi değildir. Yanlış kaynaktaki hacim darboğazı büyütür.

**CLEAN BUILD DERSI:** Kaynak önce hak, kimlik ve doğrulanabilirlikle seçilir. Scraper çoğaltmak ASAMA gerekçesi olamaz.

## 4. Scraper Stratejisi

**GOZLEM:** Toplama hattı JSONL ve eşleme ile katalog üretti. Lineage, hak kapısı ve geri çekme sonradan yetişmeye çalıştı. Google scraper kapsamını artırmak promotion boşluğunu kapatmadı.

**SONUC:** Erken scraper, erken ürün değildir. Hak unknown iken toplanan metin yük olur.

**CLEAN BUILD DERSI:** Yeni toplama, kaynak politikası ve publication kapısı olmadan açılmaz. Hacim hedefi kalite hedefinin önüne geçmez.

## 5. Google Yorumlari ve NLP

**GOZLEM:** 19.609 yorumun neredeyse tamamı Google Maps'tendi. Haklar unknown iken gerçek yorum→aday yolu kapatıldı. Public DTO'dan ham metni ayırmak ayrı ve geç bir iş oldu.

**SONUC:** Yorum adedi fact coverage demek değildi. Metin içerde olsa bile public hak doğmaz.

**CLEAN BUILD DERSI:** Google yorumları yalnız internal offline NLP girdisi olabilir. Raw review, reviewer identity ve public review score yok. Request-time ağır NLP yok.

## 6. Generic Sentiment

**GOZLEM:** Genel BERT duygu ve profil skorları yer kalitesi gibi kullanıldı. “Güzel / kaliteli / en iyi” uygunluk yerine geçti.

**SONUC:** Generic sentiment suitability değildir. Genel beğeni, sohbet veya erişim ihtiyacını çözmez.

**CLEAN BUILD DERSI:** `generic_sentiment` ayrı türdür. Tercih, sıralama, hard constraint veya public skor girdisi olamaz.

## 7. Fact ve Experience Signal Ayrimi

**GOZLEM:** Gözlem, iddia ve duygu aynı profil alanına sıkıştı. Deneyim cümleleri varlık/yokluk gibi okundu.

**SONUC:** “Park sorunu vardı” fact değildir. Deneyimi olgu sanmak false precision üretir.

**CLEAN BUILD DERSI:** `fact`, `experience_signal` ve `generic_sentiment` ayrı durur. Experience signal hard PASS/FAIL üretmez.

## 8. Yer ve Sube Kimligi

**GOZLEM:** 150 m + isim eşiği + union-find ile otomatik kalıcı birleşim vardı. Fuzzy identity merge, sonraki claim ve NLP'yi yanlış şubeye bağladı. Canonical ilçe 1719 yerin 26'sında vardı.

**SONUC:** Koordinat veya benzer isim, aynı yer demek değildir. Hatalı birleşim downstream'i zehirler.

**CLEAN BUILD DERSI:** Şube belirsizse deneyim ve iddia birleştirilmez. Kör fuzzy merge yasaktır. Kimlik insan doğrulaması olmadan kalıcı birleşmez.

## 9. Unknown ve Eksik Veri

**GOZLEM:** Kritik aileler unknown iken parser ve arama havuzu büyük görünebiliyordu. Unknown bazen yok/false gibi tüketildi; az adayda sayı doldurma baskısı oluştu.

**SONUC:** Parser başarısı veri yeterliği değildir. Unknown'u gizleyen sistem sahte kesinlik üretir.

**CLEAN BUILD DERSI:** Unknown birinci sınıf durumdur. `unknown != false`. Kritik unknown positive match değildir. Soft preference unknown “destekleniyor” demez.

## 10. Publication ve Public Veri Siniri

**GOZLEM:** İçeride bulunan yorum, skor ve iz public API'ye sızabildi. Legacy yerler hak ve kanıt kapısından geçmeden sınırlı yayın izi taşıdı.

**SONUC:** Dahilde olmak public hak değildir. Sızıntı sonradan filter ile tam onarılamaz.

**CLEAN BUILD DERSI:** Publication ayrı kapıdır. Public yüzey allow-list'tir. Otomatik yayın yoktur.

## 11. Frontend Business Logic

**GOZLEM:** Site, kart ve akış tarafında iş kuralı sızıntısı oluştu. Görsel vitrin, karar sözleşmesinden önce olgunlaştı.

**SONUC:** Frontend'de hesaplanan uygunluk ikinci motor demektir. Kanallar ayrışır.

**CLEAN BUILD DERSI:** Frontend uygunluk hesaplamaz. Sıra, kapı ve gerekçe yalnız Karar Motorundan gelir.

## 12. Search / Kesfet / Karar Motoru Ayrimi

**GOZLEM:** Keşfet, skorlama, etiket ve ticari bonus iç içeydi. Arama ayrı aday sorumluluğu olarak durmuyordu. Recommendation gibi ikinci bir yol oluştu.

**SONUC:** Karışık skor, “neden bu yer?” sorusunu cevaplamaz.

**CLEAN BUILD DERSI:** Search aday bulur. Keşfet Search + Karar Motoru akışıdır. Tek suitability authority Karar Motorudur.

## 13. Rota Planlama

**GOZLEM:** Rota skoru ilgi, duygu, kaynak puanı ve sponsor bonusunu karıştırdı. Zorunlu durak skora gömüldü. Haversine ve sabit hız estimate'leri plan gerçeği gibi durdu.

**SONUC:** Planning estimate fact değildir. Rota motoru uygunluk otoritesi olamaz.

**CLEAN BUILD DERSI:** Route Engine yalnız zaman/hareket planlar. Suitability'yi yeniden hesaplamaz. Estimate fact gibi sunulmaz.

## 14. Gunluk Rota ve Cok Gunluk Gezi Ayrimi

**GOZLEM:** Prototip 1–14 gün üretti; öğün slotları ve otomatik kayıt vardı. Günlük karar ile tatil planı aynı nesne oldu.

**SONUC:** Gün sayısını artırmak Akıllı Gezi üretmez. Küçük karar gereksiz büyür.

**CLEAN BUILD DERSI:** Günlük Akıllı Rota != Akıllı Gezi. Çok günlük gezi ayrı kapsam kararıdır; MVP dışıdır.

## 15. Migration Borcu

**GOZLEM:** Alembic zinciri prototip borcu taşıdı. Head 0016 iken güvenli baseline değildi; sarmalanmış transaction, korumalı downgrade ve canlı sürüm belirsizliği vardı.

**SONUC:** 0016 migration temiz baseline değildir. Eski şema üzerine “bir tur daha” güvenli başlangıç sayılmaz.

**CLEAN BUILD DERSI:** Clean build kendi şemasını ihtiyaç doğunca kurar. Legacy migration zinciri taşınmaz.

## 16. Dokuman Karmasasi

**GOZLEM:** `docs/`, `plan/`, `dokumanlar/` ve kök README aynı anda konuştu. Onlarca kabul kaydı, “hangi dosya kazanır?” karmaşası üretti. Belge varlığı uygulama veya araştırma sanıldı.

**SONUC:** Belge fazlalığı authority confusion yarattı. Uzun öz eleştiri, kısa kuralın yerini tutmadı.

**CLEAN BUILD DERSI:** Canonical belge az ve sahipli olur. README ve AGENTS ikinci ürün kaynağı olmaz. Karar kaydı olmadan kural değişmez.

## 17. Mega Prompt ve Agent Kullanimi

**GOZLEM:** Ürün, veri ve hak netleşmeden büyük ajan görevleri kod, UI ve araştırma momentum'u üretti. Fazlar “tamamlandı” görünürken ürün geçişi NO-GO kaldı.

**SONUC:** Momentum, netlik değildir. Mega görev borcu gizler.

**CLEAN BUILD DERSI:** Çalışma sırası bozulmaz: ihtiyaç → davranış → veri → kaynak → domain → backend → test → frontend. Ürün kilitlenmeden framework ve Hero üretilmez.

## 18. UI ve Hero'nun Erken Yapilmasi

**GOZLEM:** Scroll Hero, tasarım sistemi ve vitrin ekranları karar verilebilir veri ve publication kapısından önce geldi.

**SONUC:** Final UI, eksik kararı gizler. Erken güzellik, yanlış kapsamı meşrulaştırır.

**CLEAN BUILD DERSI:** Premium Hero ve final tasarım MVP dışıdır. UI, yetkili sonucu göstermek için gelir; ürünü tanımlamak için değil.

## 19. Test ve Invariantlar

**GOZLEM:** Yeşil testler parser, HTTP ve lint'i öne çıkardı. Sponsorun skoru etkilememesi, unknown'un true olmaması, public sızıntı yasağı sonradan invariant olarak kilitlenmek zorunda kaldı.

**SONUC:** “Test geçti” ürün invariantı demek değildir. Yanlış şeyi test etmek güven üretir.

**CLEAN BUILD DERSI:** Invariant testleri zorunludur: hard constraint telafi edilmez; unknown positive match değildir; sponsor organic kararı değiştirmez; yasak public alan çıkmaz; zayıf adayla kota dolmaz.

## 20. Yeni Projeye Tasinmayacak Implementasyonlar

**GOZLEM:** Legacy'de taşınmaya aday görünen parçalar: duygu/profil skorlama, sponsor bonusu, fuzzy merge, çok günlük otomatik rota, public yorum yüzeyi, 0016 şema, Hero vitrin, dağınık belge otoritesi.

**SONUC:** Çalışan prototip, kabul edilmiş ürünün implementasyonu değildir. Kopyalanan kod, kopyalanan yanlıştır.

**CLEAN BUILD DERSI:** Legacy implementasyon kopyalanmaz. Yeni sistemi yalnız canonical ürün sözleşmeleri bağlar. Bu belge tarihsel ders ve uyarı kaynağıdır. Kod gerektiğinde canonical sözleşmelere göre sıfırdan yazılır.
