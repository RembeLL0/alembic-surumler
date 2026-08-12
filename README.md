# Alembic — sürümler

Bu depo yalnızca **Alembic**'in sürüm dosyasını ve güncelleme paketlerini
barındırır. Uygulamanın kaynak kodu burada değildir.

## Ne işe yarar

Alembic her açılışta buradaki `surum.json` dosyasını okur. Yeni bir sürüm
varsa haber verir; sürüm zorunlu ilan edilmişse eski sürümle devam
edilemez, güncelleme kurulmadan uygulama açılmaz.

## surum.json

```json
{
  "surum": "0.2.0",
  "en_az_surum": "0.2.0",
  "adres": "https://github.com/RembeLL0/alembic-surumler/releases/download/v0.2.0/Alembic-Guncelleme-0.2.0.exe",
  "sha256": "...",
  "boyut": 1073741824,
  "notlar": "Kullanıcıya gösterilecek kısa açıklama."
}
```

| Alan | Anlamı |
|---|---|
| `surum` | Yayımlanan en son sürüm |
| `en_az_surum` | Kullanılabilecek en düşük sürüm. Bundan eskisi açılmaz. Boş bırakılırsa güncelleme yalnızca hatırlatma olur |
| `adres` | Güncelleme paketinin indirme bağlantısı |
| `sha256` | Paketin özeti. Uygulama indirdiği dosyayı bununla doğrular, tutmazsa çalıştırmaz |
| `boyut` | Bayt cinsinden boyut, ilerleme çubuğu için |
| `notlar` | Kullanıcıya düz metin olarak gösterilir |

## Güvenlik

Uygulama indirdiği dosyayı çalıştırdığı için üç kural uygular:

1. Adres `https` olmalı.
2. İndirme yalnızca GitHub konaklarından kabul edilir — bu dosya ele
   geçirilse bile indirme başka bir sunucuya yönlendirilemez.
3. İndirilen dosyanın SHA-256 özeti burada yazandan farklıysa dosya silinir
   ve kurulum başlatılmaz.

## İlk kurulum

Güncelleme paketleri model içermez (model ~2,9 GB ve değişmiyor). Uygulamayı
ilk kez kuracaklar için tam kurulum dosyası ayrıca paylaşılır.
