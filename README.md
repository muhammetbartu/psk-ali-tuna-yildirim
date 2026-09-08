# Psk. Ali Tuna Yıldırım — Bireysel Psikolog Sitesi

Koyu kahverengi zeminli, açık krem tipografili tek sayfalık tanıtım sitesi. Kurulum
veya derleme adımı yok; düz HTML, CSS ve JavaScript ile çalışır.

## Dosyalar

| Dosya | İçerik |
| --- | --- |
| `index.html` | Sayfa yapısı, tüm metinler ve SEO etiketleri |
| `kvkk.html` | KVKK aydınlatma metni ve gizlilik politikası |
| `styles.css` | Renk paleti, tipografi ve düzen |
| `script.js` | Mobil menü, kaydırma efektleri, iletişim formu |
| `favicon.svg` | Tarayıcı sekmesi simgesi |
| `robots.txt` | Arama motorları için erişim izni |

## Yerelde açmak

`index.html` dosyasını çift tıklayarak tarayıcıda açabilirsiniz. Yerel sunucu ile
çalıştırmak isterseniz:

```bash
python3 -m http.server 8000
```

Ardından `http://localhost:8000` adresini açın.

## Yer tutucular

Yer tutucu kalmadı. İletişim bilgileri ve form endpoint'i gerçek değerlerle
doldurulmuştur. E-posta adresi değişirse `index.html` iletişim listesi ve
JSON-LD, `kvkk.html` ve `script.js` içindeki `CONTACT_EMAIL` birlikte
güncellenmelidir.

## Alan adı

Alan adı `pskalitunayıldırım.com`. Türkçe karakter içerdiği için canonical,
`og:url`, `robots.txt` ve `sitemap.xml` içinde punycode karşılığı olan
`xn--pskalitunayldrm-ilccb.com` kullanılır. Tarayıcılar adres çubuğunda yine
Türkçe hâlini gösterir.

## Form altyapısı (Formspree)

Form, "Randevu İsteği" adlı Formspree formuna bağlı:
`https://formspree.io/f/xdeopwkw` (ücretsiz plan, ayda 50 mesaj). Gönderim
`script.js` içinden `fetch` ile yapılır, sayfa yenilenmez.

Endpoint değiştirilir ve `action` değerinde yeniden `FORMSPREE_ID` yazarsa
`script.js` gönderimi sunucuya yollamayı bırakır ve ziyaretçinin e-posta
uygulamasını hazır bir mesajla açar (`mailto` yedeği).

Test ederken gerçekçi bir metin kullanın; sahte içerikli denemeleri Formspree
"Spam" sekmesine düşürür ve bildirim göndermez. Formun spam koruması, görünmeyen
`_gotcha` tuzak alanıdır.

## Yayınlamak (GitHub Pages)

Klasörü bir GitHub deposuna yükleyip **Settings → Pages** altından `main` dalı /
`/ (root)` klasörünü seçmek yeterli. Yayın adresi:

```
https://<kullanıcı-adı>.github.io/<depo-adı>/
```

Her `git push` sonrası site birkaç dakika içinde kendini günceller:

```bash
git add .
git commit -m "İçerik güncellendi"
git push
```

## Alan adı bağlamak

Alan adı alındığında, kayıt firmasının DNS panelinde kök alan adı için dört GitHub
Pages `A` kaydı ve `www` için bir `CNAME` kaydı tanımlanır:

| Tür | Ad | Değer |
| --- | --- | --- |
| A | `@` | `185.199.108.153` |
| A | `@` | `185.199.109.153` |
| A | `@` | `185.199.110.153` |
| A | `@` | `185.199.111.153` |
| CNAME | `www` | `<kullanıcı-adı>.github.io` |

Kayıt firmasının park sayfasına ait eski `A` kayıtları silinmelidir. Ardından depoya
alan adını içeren bir `CNAME` dosyası eklenir, GitHub **Settings → Pages → Custom
domain** alanına aynı adres yazılır ve **Enforce HTTPS** işaretlenir. Sertifika
birkaç dakika içinde otomatik oluşur.

Doğrulamak için:

```bash
dig +short <alan-adı> A
curl -sI https://<alan-adı> | head -1
```

## Kişiselleştirme

- **Metinler:** `index.html` içindeki bölümleri (hakkımda, çalışma alanları, SSS)
  doğrudan düzenleyin.
- **Renkler:** `styles.css` dosyasının başındaki `:root` değişkenlerini değiştirmeniz
  yeterli. `--cream` sayfa zeminini, `--brown` ana yazı rengini, `--surface` kart ve
  form zeminlerini, `--accent-deep` ise bağlantı ve buton rengini belirler.
- **Fotoğraf:** Hero bölümündeki `.portrait` alanı şu an degrade bir yer tutucudur.
  Gerçek fotoğrafı eklemek için `index.html` içindeki `<div class="portrait">` etiketini
  bir `<img src="foto.jpg" alt="Psk. Ali Tuna Yıldırım" class="portrait">` ile
  değiştirin.

## Yasal not

`kvkk.html` sayfası aydınlatma metnini ve gizlilik politikasını içerir; iletişim
formundaki zorunlu onay kutusu bu sayfaya bağlanır. Metin, Formspree ve GitHub Pages
sunucuları yurt dışında olduğu için yurt dışına aktarıma ilişkin açık rıza ifadesini de
içerir. Yayına almadan önce metindeki ad, adres ve e-posta bilgilerinin gerçek
bilgilerle güncellenmesi gerekir.
