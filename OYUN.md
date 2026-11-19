# Crazy Crescent — oyun notları

Hilal (ay) ile renkli bulutların üstünden zıplayarak sol alttan sağ üste tırmanılan, bölüm bitirme odaklı mobil platform oyunu.
Eski Google Play oyunu `air.CrazyCrescent`'in (Play'deki adı: "Maryo World (platform)") baştan yapılmış hâli.

- Kod: tek dosya `www/index.html` (saf Canvas 2D, bağımlılık yok). Sürüm: dosyadaki `SURUM` (şu an v0.8), her değişiklikte artırılır.
- Görseller kodla çizilir; sadece kapak `www/img/kapak.jpg` ve ikon/açılış `assets/` dışarıdan gelir.
- Test: `https://raw.githack.com/cemrebaou/CrazyCrescent/<commit>/www/index.html`
- Yatay oyun. Dokunmatik butonlar PC'de de görünür.

## Ekranlar
- **Yükleme:** kapak görseli soldan sağa açılır, altta "Yükleniyor %".
- **Kapak:** tam kapak görseli + "Dokun ve başla", sağ altta `TR ⇄ EN` dil butonu, sağ üstte tam ekran butonu.
- **Oyun:** sol üstte güneş (içinde bölüm no), sağ üstte canlar (ay), altında tam ekran butonu; bölüm başında "Bölüm N · Ad" yazısı; yeni bulut türü ilk kez görünce üstte ipucu.
- **Canın bitti paneli:** "Reklam izle, devam et" (ödüllü) veya "Baştan başla (1. bölüm)".
- **Bitiş:** 50. bölüm sonrası "Tebrikler!".

## Dil
- Türkçe / İngilizce. Telefon dili `tr` ise TR, değilse EN. Kapaktaki butonla değişir, `localStorage` `hilalDil`.
- Metinler `TXT.tr / TXT.en`, ipuçları `HINT_TR / HINT_EN`, bölüm adları `NAME_EN`.

## Kontroller
- Dokunmatik: sol altta ◀ ▶, ekranın sağ yarısı zıplama.
- Klavye: ← → / A D, zıplama Boşluk / ↑ / W.
- Güneşe dokunmak bölüm atlatır — sadece tarayıcı testinde, uygulamada kapalı.

## Fizik
| Değer | Sayı |
|---|---|
| Yerçekimi | 1800 |
| Zıplama hızı | 720 (≈144 px yükselir, yatayda ≈208 px gider) |
| Koşu hızı | 260 |
| Gül buluttan süper zıplama | ×1.45 (≈300 px) |
| Kahverengi sektirme | 1020 (≈290 px) |
| Adım | 1/120 sn sabit |

## Can
- Can = ay, başlangıç 3, **en fazla 5**.
- Denize düşmek **1 ay**, siyah şimşek **yarım ay** götürür (göstergede yarım ay).
- Bölüm geçince **+1 ay**, altın bulut **+1 ay** (sınır 5). Canlar sonraki bölüme taşınır.
- Denize düşünce son beyaz buluttan devam edilir.
- Canlar bitince: ödüllü reklam → aynı bölümden 3 canla devam; izlemezse **1. bölümden baştan**.
- Kayıt: `localStorage` `hilalLvl` (bölüm), `hilalCan` (can).

## Reklamlar (AdMob, sadece Android uygulamasında)
| Tür | Ne zaman | Kimlik |
|---|---|---|
| Uygulama kimliği | — | `ca-app-pub-7983529419004158~2013724249` |
| Banner | her zaman üstte, küçük standart banner 320×50 (oyun alanı banner'ın altından başlar) | `ca-app-pub-7983529419004158/4140166464` |
| Geçiş | her 5 bölümde bir, bölüm geçişinde | `ca-app-pub-7983529419004158/3254299313` |
| Ödüllü | canlar bitince devam için | `ca-app-pub-7983529419004158/7541028686` |
| Uygulama açılış | sadece arka plandan dönünce (ilk açılışta yok, en az 30 sn arayla) | `ca-app-pub-7983529419004158/9597501336` |

Tarayıcıda reklam yok; ödüllü butonu test için direkt devam ettirir.

## Bulutlar (26 tür)
| Renk | Kod | Davranış |
|---|---|---|
| Beyaz | `white` | Sağlam zemin, kayıt noktası |
| Siyah | `black` | Şimşek çakar, basınca yarım can + geri fırlatır |
| Yeşil | `green` | 3.7 sn şişer, patlar, 1.2 sn sonra küçük hâlde yeniden çıkar |
| Mavi | `blue` | Sırayla dizilir, bekler, hepsi kaybolur |
| Kırmızı | `red` | 3 kat yukarı sıçrar (96 px), sonra en alttan başlar |
| Kahverengi | `brown` | Zıplatır |
| Turuncu | `orange` | İki kol ortadan açılır, düşersin |
| Sarı | `yellow` | İki kanatlı pervane, kanatlara her açıda basılır, eğikte kayarsın |
| Turkuaz | `turq` | Asansör, aşağı-yukarı |
| Pembe | `pink` | Basınca erir, 2.2 sn sonra geri gelir |
| Mor | `purple` | İkizine ışınlar |
| Gri | `grey` | Rüzgârı alt ortasından çıkar, seni sürükler |
| Buz | `ice` | Kaygan |
| Lila | `lilac` | Sarkaç gibi sallanır |
| Altın | `gold` | +1 can (bir kez) |
| Krem | `beige` | Ağırlığınla çöker |
| Mercan | `coral` | Binince ok yönünde uçar, sonra geri döner |
| Nane | `mint` | Bulutun içinden yukarı yumuşak hava sütunu üfler, süzülürsün |
| Lacivert | `navy` | Her zıplayışta var / yok olur (yerinde zıplayarak ayarlanır) |
| Limon | `lime` | Sağa sola kayar |
| Fuşya | `magenta` | Üstünde durdukça küçülür, kaybolur |
| Şeftali | `peach` | Basınca titrer ve düşer |
| Çivit | `indigo` | Daire çizerek döner |
| Gül | `rose` | Buradan zıplayınca çok yükselirsin |
| Deniz | `sea` | Sıra sıra dalga gibi iner çıkar |
| Gökkuşağı bulutu | `finish` | Bölüm sonu: buluta bin, ileri git, gökkuşağına tırman |

Gökkuşağı başta ve sonda bulutun içinden tek noktadan çıkıp açılır.

## Bölümler (50)
- 1–10 elle tasarlandı (`LV` dizisi), her biri yeni bulutlar tanıtır:
  1 Sabah · 2 Öğle · 3 İkindi · 4 Gün Batımı · 5 Alacakaranlık · 6 Şafak · 7 Kiraz Bahçesi (yaprak yağar) · 8 Kar Diyarı (kar yağar) · 9 Yıldızlı Gece · 10 Kuzey Işıkları
- 11–50 `genLevel(n)` ile üretilir: her bölüm bir öncekinden **%5 daha uzun** (10. bölüm 20 parça, 50. bölüm ≈141 parça).
  İlk 10 bölümden alınmış güvenli parçalardan seed ile seçilir; ilerledikçe hızlar (×1→×1.5) ve siyah bulut sıklığı artar.
  Temalar 10'da bir tekrar eder (Sabah II, Şafak III …).
- Bölüm sırası formatı: `['tür', boşluk, yükseliş, genişlik, {ayar}]`, önceki bulutun sağ kenarına göre.

## Android / Play
- **Bu bir telefon oyunu:** asıl ürün AAB (Google Play) + telefona kurulan APK; tarayıcı sürümü sadece test için.
- **Tam ekran:** uygulama her zaman saat/pil/gezinme çubuğu gizli, kenarlarda boşluk olmadan tüm ekranı kaplar (MainActivity immersive + çentik modu ALWAYS + WebView kenar boşlukları sıfır; `capacitor.config.json`: `adjustMarginsForEdgeToEdge: disable`, `SystemBars.insetsHandling: disable, hidden: true`).
- **AAB alırken (her seferinde, söylenmese de):** uygulamada tam ekran butonu olmaz (sadece tarayıcıda görünür); optimizasyon açık: R8 kod küçültme (`minifyEnabled true`) + kaynak küçültme (`shrinkResources true`), Capacitor/AdMob sınıfları `proguard-rules.pro` ile korunur; `mapping.txt` AAB ile birlikte artifact'e konur (Play Console → App bundle explorer → kod gizleme açma dosyası olarak yüklenir).
- **Donanım özellikleri her zaman isteğe bağlı** (`android:required="false"`: screen.landscape, screen.portrait, touchscreen) — Play'deki "zorunlu donanım özelliği" hatası çıkmasın.
- Capacitor 8 + `@capacitor-community/admob`, paket `air.CrazyCrescent`, uygulama adı "Crazy Crescent".
- AAB **sadece elle** üretilir: GitHub → Actions → Android AAB → Run workflow (kullanıcı "tamam" deyince).
- İmza secret'ları: `KEYSTORE_BASE64`, `KEYSTORE_PASSWORD`, `KEY_ALIAS` (Play'in beklediği SHA1 `88:71:61:AF:…:0D:D4:8C`).
- Sürüm kodu = 2003000 + çalıştırma no (Play'deki en yüksek eski kod 2002000).
- İkon ve açılış: `assets/` (kullanıcının verdiği hilal-gökkuşağı görseli), arka plan `#9a8ee6`.
- `android-ayar/ayarla.py`: yatay ekran, gerçek tam ekran (MainActivity immersive: saat ve gezinme çubuğu gizli), AdMob kimliği, imza, sürüm, SDK 36.
- Uygulamada tam ekran butonu gizli (sadece tarayıcıda görünür).
