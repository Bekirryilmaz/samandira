# SAMANDIRA

## Proje Nedir?

SAMANDIRA, insanların o anki durumuna uygun az sayıda yeri gerekçesi, ödünü ve bilinmeyenleriyle bulmasına yardım eden bir karar ürünüdür.

Bu dosya ürün kaynağı değildir. Ürün gerçeği için [belgeler/urun/urun-sozlesmesi.md](belgeler/urun/urun-sozlesmesi.md) okunur.

## Clean Build

Bu repo eski `gezi_bot` kodunun devamı veya taşıması değildir. Yeni sistem temiz temel üzerine kurulur. Legacy implementasyon kopyalanmaz.

## Repository Gercegi

| Rol | Repo |
| --- | --- |
| Aktif kod ve belge gerçeği | [Bekirryilmaz/samandira](https://github.com/Bekirryilmaz/samandira) |
| Salt-okunur referans | [Bekirryilmaz/gezi_bot](https://github.com/Bekirryilmaz/gezi_bot) |

Yazma, commit ve push yalnız aktif repoda ve yalnız açık kullanıcı isteğiyle yapılır.

## Mevcut Asama

ASAMA 0 — temiz temel belgeler. Uygulama kodu, framework kurulumu ve veri hattı henüz yoktur.

## Belgelere Nereden Baslanir?

[belgeler/00-buradan-basla.md](belgeler/00-buradan-basla.md)

## Temel Calisma Kurali

Sıra şudur: kullanıcı ihtiyacı → ürün davranışı → gerekli veri → veri kaynağı → domain sözleşmesi → backend/API → test → frontend.

Ajanların operasyonel kuralları [AGENTS.md](AGENTS.md) içindedir.

## Legacy Proje

Eski projedeki dersler canonical değildir. Yalnız uyarı olarak okunur: [belgeler/legacy/eski-projeden-dersler.md](belgeler/legacy/eski-projeden-dersler.md)
