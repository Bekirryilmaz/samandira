# SAMANDIRA MVP Kapsami

## 1. Belgenin Amaci ve Otoritesi

Bu belge, [urun-sozlesmesi.md](./urun-sozlesmesi.md) altındaki MVP sınırıdır.

Ne doğrulanacağını, hangi yetenek adaylarının çekirdekte olduğunu ve nelerin şimdilik dışarıda kaldığını söyler. Desteklenen coğrafya ve amaç listesini veri olmadan resmi yetenek olarak kilitlemez.

## 2. MVP'nin Dogrulayacagi Ana Hipotez

Kullanıcıya çok seçenek göstermek yerine, bağlamına uygun az sayıda seçeneği güvenilir gerekçeler ve bilinmeyenlerle sunmak gerçek karar yükünü azaltır.

MVP'nin işi bu hipotezi, savunulabilir veri ve dürüst sonuçlarla sınamaktır. Katalog doldurmak, şehir sayısını artırmak veya vitrin UI üretmek hipotezi doğrulamaz.

## 3. MVP'de Olmasi Gereken Yetenekler

Başlangıç yetenek adayları:

- **Arama** — yer veya ihtiyaç ifadesinden aday bulur
- **Keşfet** — Search + Karar Motoru ile az sayıda gerekçeli seçenek üretir
- **Yer detayı** — bir yerin bu ziyaret için ne anlama geldiğini, ödünü ve bilinmeyenlerini gösterir
- **Bugün Ne Yapalım** — düşük eforlu girdiyi yapılandırılmış karar bağlamına çevirir
- **Günlük Akıllı Rota** — Karar Motorundan geçmiş yerleri bir günün zaman/hareket problemi olarak planlar

Bunlar resmi destek kapsamı değildir. Bir yetenek, §7 ölçütünü geçmeden MVP vaadi sayılamaz. Kavram ayrımları [domain-ve-karar-sozlesmesi.md](./domain-ve-karar-sozlesmesi.md) içindedir.

## 4. MVP Disinda Kalanlar

MVP'ye girmez:

- 81 il zorunluluğu
- çok günlük Akıllı Gezi
- tüketici hesabı zorunluluğu
- public review platformu
- Premium
- ödeme
- booking
- sosyal ağ
- sponsorlu organic ranking
- request-time review NLP
- microservices
- Redis / Kafka / Elastic / vector DB
- final premium Hero / tasarım

Bunlar “sonra mutlaka yapılacak” listesi de değildir. Her biri ayrı ihtiyaç, veri ve karar kaydı ister.

## 5. Desteklenen Cografya Durumu

Samsun güçlü bir başlangıç hipotezidir. Canonical kesin destek değildir.

Bir coğrafya ancak ilgili yer kimliği, yayımlanabilir iddia ve dürüst boş sonuç üretilebildiğinde desteklenmiş sayılır. Kayıt sayısı şehir açmaz.

## 6. Desteklenen Amaclar Durumu

Legacy'de kahve, yemek veya tarih gibi görünen amaçlar araştırma girdisidir. Official capability list değildir.

Bir amaç, o amaç için gerekli iddialar bilinmiyorken “destekleniyor” yazılamaz. Amaç listesi ASAMA 1'de veri yeterliğiyle kesinleşir.

## 7. Bir Yetenegin MVP'ye Girebilme Kriteri

Yetenek ancak şu koşulların hepsi varsa MVP'ye girer:

1. [urun-sozlesmesi.md](./urun-sozlesmesi.md) içindeki karara yardım eder.
2. Gerekli veri türü ve kaynağı bellidir; hak ve yayın kapısı [veri-ve-yayin-sozlesmesi.md](./veri-ve-yayin-sozlesmesi.md) ile uyumludur.
3. Unknown, ödün ve boş sonuç dürüstçe gösterilebilir.
4. Zayıf adayla kota doldurmadan çalışabilir.
5. Frontend'e iş kaçırmadan, tek Karar Motoru ile üretilir.

Veri yoksa yetenek daraltılır veya ertelenir. Ekran varlığı yeteneği açmaz.

## 8. MVP Kabul Kriterleri

MVP, aşağıdaki olmadan kabul edilmez:

- Az sayıda seçenek; her seçenekte neden, ödün ve bilinmeyen
- Hard constraint ihlalinde veya kritik unknown durumunda positive match yok
- Sponsorun organic sıra veya uygunluğu değiştirmemesi
- Public yüzeyde ham yorum, yorumcu kimliği ve sentiment skoru yok
- “Uygun seçenek yok”un geçerli ve kullanılabilir sonuç olması
- Günlük rotanın suitability'yi yeniden icat etmemesi

Kayıt hacmi, test yeşili veya görsel tamamlanmışlık kabul kanıtı değildir.

## 9. ASAMA 1'de Kesinlesecek Konular

ASAMA 1 kilitler; bu belge spekülasyon yapmaz:

- İlk desteklenecek coğrafyanın gerçek sınırı
- İlk desteklenecek amaçların gerçek listesi
- Hangi yetenek adaylarının §7'yi geçtiği
- İlk veri kaynakları ve hak durumu
- Pilot yer havuzunun kalite eşiği

Bu konular kilitlenmeden framework kurulumu ürün vaadini genişletmiş sayılmaz.
