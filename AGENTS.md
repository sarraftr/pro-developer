# SarrafPro Developer — dokümantasyon çalışma talimatları

Bu depo SarrafPro Dış API (v1) geliştirici dokümantasyonudur. Sayfalar MDX, yapılandırma `docs.json`, site motoru Mintlify'dır.

## Dil ve üslup

- Tüm içerik **Türkçe**dir. Kod, alan adları ve HTTP terimleri İngilizce kalır.
- Üslup profesyonel, doğrudan ve ikinci tekil şahıstır ("gönderin", "alırsınız").
- Cümleler kısadır, bir cümlede bir fikir vardır. Başlıklarda cümle düzeni kullanılır.
- Dosya adları, alanlar, parametreler ve kod referansları `backtick` içinde yazılır.

## Sayfa iskeleti

Her uç sayfası aynı sırayı izler:

1. Kaynağın ne işe yaradığı — bir paragraf
2. Uç başlığı: `` `METHOD /v1/yol` — kısa açıklama ``
3. `curl` istek örneği
4. Parametre / gövde alanı tablosu
5. Gerçekçi JSON cevap örneği
6. Hata tablosu (HTTP + `error.code` + açıklama)
7. Varsa uyarı/not bileşenleri

Ortak kurallar (kimlik doğrulama, zarf, sayfalama, hata kodları) tekrar edilmez; [Genel Bakış](api-reference/genel-bakis.mdx) sayfasına bağlantı verilir.

## Gizlilik sınırı — zorunlu

Dokümana ve OpenAPI dosyasına **asla** yazılmaz:

- İç alan adları, geliştirme ortamı adresleri, yerel host adları
- IP adresleri, altyapı ve sunucu topolojisi bilgisi
- Kimlik bilgileri, API anahtarları, örnek gerçek anahtarlar
- Veritabanı koleksiyon adları, iç modül adları, iç kayıt damgaları

Örneklerde yalnız canlı ortam adresi (`https://api.sarraf.pro`) ve temsilî değerler kullanılır.

## OpenAPI dosyası

`api-reference/openapi.json` bu depoda **elle düzenlenmez**. API deposundaki `project/sarraf/docs/api-v1.openapi.json` kaynaktır; değişiklik orada yapılır ve buraya kopyalanır. İki kopya birebir aynı olmalıdır.

## Değişiklik disiplini

- Sayfa adresleri (slug) korunur. Yeniden adlandırma gerekiyorsa `docs.json` içinde `redirects` tanımlanır.
- API sözleşmesi değiştiğinde ilgili sayfa **aynı işte** güncellenir; doküman ile sözleşme arasında sapma bırakılmaz.
- Yeni uç eklendiğinde: kaynak sayfası + `docs.json` gezinme + spec kopyası birlikte güncellenir.
- Yayına alınmamış veya kapsam dışı bırakılmış uçlar dokümana yazılmaz.
