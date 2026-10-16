# Optik Transfer v0.2

İnternet, Bluetooth veya Wi‑Fi bağlantısı kullanmadan, verici ekranında gösterilen renkli kareleri alıcı telefonun kamerasıyla okuyarak kısa metin aktarmayı deneyen web prototipi.

## Dosyalar
- `index.html`: Ana menü
- `verici.html`: Metni renkli kareler halinde gösterir
- `alici.html`: Kamera görüntüsünden kareleri okur ve metni birleştirir
- `shared.js`: İki tarafın ortak protokolü ve CRC16-CCITT hata kontrolü

## Çalıştırma
1. Dört dosyayı aynı klasörde tutun.
2. GitHub Pages gibi HTTPS sağlayan bir yere yükleyin. Kamera erişimi için HTTPS gerekir (localhost da desteklenir).
3. İki telefonda da aynı siteyi açın.
4. İlk telefonda **Verici** sayfasına girip metni yazın ve **Başlat**'a basın.
5. İkinci telefonda **Alıcı** sayfasını açın, kamera iznini verin ve kareyi ortadaki kılavuza hizalayın.
6. Telefonları sabit tutun; ilk testte parlaklığı artırın, yansımayı azaltın ve yaklaşık 5–15 cm mesafeyi deneyin.

## Protokol sınırları
- 8×8 = 64 hücre; hücre başına 2 bit, toplam 16 bayt/frame.
- 6 bayt başlık, 8 bayt veri, 2 bayt CRC16-CCITT.
- Alıcı ile uyum için bu sürümde en fazla 2.000 frame / 16.000 UTF‑8 bayt kabul edilir.
- Varsayılan hız 3 frame/saniye olarak ayarlanmıştır. Gerçek hız kamera, ekran, ışık ve odak koşullarına bağlıdır.

## Bilinen sınırlamalar
- Bu bir deneysel MVP'dir; farklı telefonlarda ve ışık koşullarında test edilmesi gerekir.
- Renk kalibrasyonu ve perspektif düzeltme henüz yoktur. Kareler eğik, çok küçük veya yansımalı görünürse okuma başarısız olabilir.
- Kayıp kareler otomatik tekrar istemiyle geri alınmaz; verici sürekli döngü yaptığı için alıcı açık kaldıkça tekrar yakalamayı dener.
- Yalnızca metin aktarımı vardır; resim/dosya aktarımı bu sürümde yoktur.
