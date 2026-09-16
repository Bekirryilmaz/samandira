# Sistem Sinirlari

## 1. Belgenin Otoritesi

Bu belge, [urun-sozlesmesi.md](./urun-sozlesmesi.md) altındaki mimari sınır sözleşmesidir.

Sorumlulukların nerede duracağını tanımlar. Ürün vaadini [urun-sozlesmesi.md](./urun-sozlesmesi.md), karar kurallarını [domain-ve-karar-sozlesmesi.md](./domain-ve-karar-sozlesmesi.md), veri kapılarını [veri-ve-yayin-sozlesmesi.md](./veri-ve-yayin-sozlesmesi.md) değiştirmez.

## 2. Mimariyi Tureten Urun Ihtiyaclari

Mimari şu ihtiyaçlardan türer:

- Az sayıda gerekçeli seçenek üretmek
- Unknown ve ödünü gizlemeden taşımak
- Aynı karar kuralını bütün kanallara vermek
- Ham veriyi public yüzeyden ayırmak
- Ağır dil işlemini istek anından çıkarmak

Teknoloji hevesi mimari gerekçe değildir.

## 3. Mantiksal Sistemler

Başlangıçta bunlar ayrı deploy birimi olmak zorunda değildir. Ayrı sorumluluktur:

- Yer kimliği
- Kaynak, gözlem ve hak
- İddia ve publication
- Arama (aday)
- Karar Motoru (uygunluk)
- Günlük rota planlama (zaman/hareket)
- API
- Web sunumu
- Offline veri hazırlama

İkinci bir uygunluk motoru oluşmaz.

## 4. Frontend Sorumlulugu

Frontend:

- kullanıcı girdisini ve bağlamı backend'e taşır
- yetkili sonucu, boş hali ve hatayı gösterir
- neden, ödün ve bilinmeyeni gizlemez
- erişilebilir gezinme ve durum restorasyonu sağlar

## 5. Frontend'in Yasak Oldugu Kararlar

Frontend şunları yapmaz:

- uygunluk hesabı
- hard constraint veya unknown kapısı
- organic sıra üretimi
- sponsor veya görsel üstünlükle yeniden sıralama
- fact uydurma veya LLM ile yer icadı
- public'e yasak alanları gösterme

## 6. Backend Sorumlulugu

Backend:

- kimlik, hak, iddia ve yayın kapılarını korur
- Search ve Karar Motorunu çalıştırır
- public ve internal sözleşmeleri ayırır
- rota planına yalnız Karar Motorundan geçmiş yerleri verir
- estimate'i fact olarak işaretlemez

## 7. Merkezi Karar Motoru

Karar Motoru tek suitability authority'dir.

Web, gelecekteki mobil istemci ve dahili araçlar aynı kuralı kullanır. Kanal, “bu yüzeyde skor biraz farklı olsun” diyemez. Rota planlama bu otoriteyi devralmaz.

## 8. API Siniri

API, kanallara aynı anlamı taşır.

Public DTO allow-list'tir. Ham yorum, reviewer identity, dahili skor, model confidence ve sentiment yüzdesi public sözleşmeye girmez. Admin/internal yüzey public yüzeyle paylaşılmaz.

## 9. Request-Time ve Offline Isler

Request-time:

- bağlamı anlama
- aday bulma
- Karar Motoru
- günlük planlama
- yetkili sonucu anlatma

Offline:

- kaynak toplama
- hak kontrolü
- ağır NLP / gözlem adayı üretimi
- iddia hazırlığı ve publication kuyruğu
- freshness ve geri çekme yayılımı

Request-time ağır NLP yoktur. Her aramada bütün yorumlar yeniden okunup yer kişiliği uydurulmaz.

## 10. Veri Depolama Siniri

Kalıcı hakikat uygulama belleğinde veya frontend cache'inde durmaz.

Runtime/private veri repo ürün ağacına karışmaz; kökte `/veri/`, `/cikti/`, `/cache/` kullanılır. İndeks yeniden üretilebilir. Production data açık izin olmadan değişmez.

## 11. Gelecekte Mobil Istemci

Mobil istemci yeni karar motoru değildir.

Aynı API anlamını tüketir. Offline okuma gerekirse yalnız yayımlanmış ve kayıtlı temel içeriği, aynı yasaklarla taşır. Mobil varlık, ürün kuralını gevşetmez.

## 12. Baslangic Teknik Yonu

Mevcut ihtiyaçlara dayalı başlangıç yönü:

| Katman | Yön |
| --- | --- |
| Web | Next.js |
| Backend | FastAPI modular monolith |
| Veri | PostgreSQL + PostGIS |
| Offline veri işlemleri | Python |

Bu seçimler değişmez teknoloji yasası değildir. Gerekirse `belgeler/kararlar/` kaydı ile revize edilebilir. Seçimin varlığı bu ASAMA'da kurulumu yetkilendirmez.

## 13. Gereksiz Karmasiklik Yasagi

İhtiyaç ve ölçülmüş yük olmadan eklenmez:

- microservice
- Redis
- Kafka
- Elastic
- vector DB

Erken “ölçek için” altyapı, ürün netliğini ertelemek için kullanılmaz.

## 14. Mimari Degisiklik Kurali

Sorumluluk sınırı, request-time/offline ayrımı veya Karar Motoru tekliği değişecekse:

1. hangi ürün ihtiyacının değiştiği yazılır
2. bu belge güncellenir
3. gerekirse karar kaydı açılır

Kodun kolay gelmesi veya legacy'de benzer klasör olması gerekçe değildir. `web/`, `sunucu/`, `veri_hatti/`, `testler/`, `altyapi/` yalnız gerçek içerik ihtiyacında açılır.
