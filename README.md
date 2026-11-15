# Crazy Crescent

Hilal ile renkli bulutların üstünden zıplayarak gökkuşağına ulaşılan platform oyunu. Oyun tek dosya: `www/index.html` (sürüm `SURUM`), tüm görseller kodla çiziliyor. Android: Capacitor + AdMob, paket `air.CrazyCrescent` (eski AIR oyununun güncellemesi). AAB sadece elle üretilir: Actions → Android AAB → Run workflow. İmza: secrets `KEYSTORE_BASE64`, `KEYSTORE_PASSWORD`, `KEY_ALIAS`; sürüm kodu = 2003000 + çalıştırma no. (Play deki en yüksek kod 2002000)

## Kontroller
- Dokunmatik: sol altta ◀ ▶, ekranın sağ yarısı zıplama
- Klavye: ok tuşları / A-D, boşluk ile zıplama
- Ekran butonları PC'de de görünür
- Sağ üstte, canların altında tam ekran butonu (oyunu yatay kilitler)
- Altta 50 px banner reklam alanı ayrıldı
- Can = ay. Denize düşmek 1 ay, şimşek yarım ay götürür; bölüm geçince +1 ay (en fazla 9), canlar sonraki bölüme taşınır
- Canlar bitince: ödüllü reklam izle → aynı bölümden 3 canla devam; izlemezsen 1. bölümden baştan
- Sol üstteki güneşe dokunmak sonraki bölüme atlar (sadece tarayıcı testinde, uygulamada kapalı)

## Bulutlar
| Renk | Davranış |
|---|---|
| Beyaz | Sağlam zemin |
| Siyah | Şimşek çakar, üstüne basınca can götürür |
| Yeşil | Şişer, patlar, yeniden oluşur |
| Mavi | Sırayla dizilir, sonra yol kaybolur |
| Kırmızı | 3 kat yukarı sıçrar, sonra en alttan başlar |
| Kahverengi | Zıplatır |
| Turuncu | İki kol ortadan açılır, düşersin |
| Sarı | Tek kanatlı pervane gibi döner |
| Turkuaz | Asansör |
| Pembe | Basınca erir, sonra geri gelir |
| Mor | İkizine ışınlar |
| Gri | Rüzgârı sürükler |
| Buz mavisi | Kaygan |
| Lila | Sarkaç gibi sallanır |
| Altın | +1 can |
| Krem | Ağırlıkla çöker |
| Mercan | Binince ok yönünde uçar |
| Nane | Yukarı üfler |
| Lacivert | Her zıplayışta var / yok olur |
| Limon | Sağa sola kayar |
| Fuşya | Üstünde durdukça küçülür, kaybolur |
| Şeftali | Basınca düşer |
| Çivit | Daire çizerek döner |
| Gül | Buradan zıplayınca çok yükselirsin |
| Deniz | Dalga gibi iner çıkar |
| Gökkuşağı bulutu | Bölüm sonu |

## Reklamlar (AdMob)
- Banner: her zaman altta
- Geçiş: her 5 bölümde bir
- Ödüllü: canlar bitince devam etmek için
- Açılış: sadece uygulamaya geri dönünce (ilk açılışta gösterilmez)

## Bölümler
50 bölüm. 1-10 elle tasarlandı; 11-50 her biri bir öncekinden %5 daha uzun, hazır parçalardan seed ile üretilir, hızlar giderek artar. Temalar 10'da bir tekrar eder (Sabah II, III ...).
1 Sabah · 2 Öğle · 3 İkindi · 4 Gün Batımı · 5 Alacakaranlık · 6 Şafak · 7 Kiraz Bahçesi (yaprak yağar) · 8 Kar Diyarı (kar yağar) · 9 Yıldızlı Gece · 10 Kuzey Işıkları
