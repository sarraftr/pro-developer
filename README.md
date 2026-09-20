# SarrafPro Developer

[SarrafPro Dış API (v1)](https://api.sarraf.pro) geliştirici dokümantasyonunun kaynak deposu. Site [Mintlify](https://mintlify.com) ile yayınlanır.

## Depo yapısı

| Yol | İçerik |
|---|---|
| `docs.json` | Site yapılandırması: gezinme, tema, API referansı sekmesi |
| `index.mdx` | Giriş sayfası |
| `quickstart.mdx` | Hızlı başlangıç |
| `api-reference/genel-bakis.mdx` | Tüm uçlarda geçerli ortak sözleşme |
| `api-reference/*.mdx` | Kaynak rehberleri (müşteriler, banka, faturalar, giderler) |
| `api-reference/openapi.json` | Makine-okunur sözleşme (OpenAPI 3.0.3) |

## OpenAPI dosyası

`api-reference/openapi.json` **bu depoda elle düzenlenmez.** Kaynağı API deposundaki `project/sarraf/docs/api-v1.openapi.json` dosyasıdır; her API değişikliğinde oradan kopyalanır. İki kopyanın birebir aynı olması gerekir:

```bash
diff -q ../api/project/sarraf/docs/api-v1.openapi.json api-reference/openapi.json
```

## Yerel önizleme

```bash
npm i -g mint
```

```bash
mint dev
```

Önizleme `http://localhost:3000` adresinde açılır.

## Yayın

`main` dalına yapılan her push, Mintlify GitHub uygulaması üzerinden canlıya taşınır. Değişiklikleri push etmeden önce yerel önizlemede kontrol edin.

## Yazım kuralları

Sayfa iskeleti, üslup ve gizlilik kuralları [AGENTS.md](AGENTS.md) dosyasındadır. Özetle:

- Dil Türkçe, üslup profesyonel ve doğrudan.
- Her uç aynı iskelete oturur: ne işe yarar → istek → parametreler → cevap → hatalar.
- Dokümana **iç alan adları, IP adresleri, kimlik bilgileri ve geliştirme ortamı bilgileri yazılmaz**; yalnız canlı ortam bilgileri yer alır.
- Sayfa adresleri (slug) korunur; yeniden adlandırma gerekiyorsa `docs.json` içinde yönlendirme tanımlanır.

---

© SarrafPro. Tüm hakları saklıdır.
