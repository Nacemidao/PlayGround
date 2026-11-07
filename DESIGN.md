# Kül Yemini — konsept ve sistem tasarımı

## Vizyon

**Kül Yemini**, Android ve iOS için portre değil yatay kullanımda tasarlanan, tek oyunculu, üstten görünümlü 2D taktiksel bir fantezi Aksiyon RPG'sidir. Oyuncu külle kaplı sınır bölgelerinde kısa ve tekrar oynanabilir keşiflere çıkar; düşman saldırılarını okuyup konumlanır, kendi saldırı ve yeteneklerini zamanlar, ekipmanını geliştirir. Her savaş oyuncu girdisiyle başlar: otomatik saldırı, otomatik hedefleme/ateş etme, dalga tabanlı hayatta kalma veya AFK ilerlemesi yoktur.

**Duygu:** okunaklı, tehlikeli ama adil çatışma; bir sonraki ganimet için “bir keşif daha”. Anlatı çevre ve birkaç kamp NPC'siyle sınırlıdır. Yan görevler hikâyenin önüne geçmeden gelişim duvarlarını yumuşatır.

## Oynanış döngüsü

1. Kamp veya keşif alanında hedef / isteğe bağlı tehlike mührü seç.
2. Kül Geçidi gibi kompakt bir zindanda ayrık düşman kümelerini gözle; yaklaş, saldırı telegraph'ını oku, elle kaçın ve yetenek penceresini kullan.
3. Düşen ekipman ve malzemeyi yaklaşarak etkileşim tuşuyla topla.
4. Ganimeti karşılaştır; ustalık ve seviye kazan; isteğe bağlı toplama görevini bitir.
5. Demirhanede üret, yetenek ağında uzmanlaş ve daha yüksek riskli keşfi seç.

### Çatışma

- **Kontrol:** Sol sanal joystick hareket; sağ başparmak kümesi basılı tutulan temel saldırı, iki aktif yetenek, atılma ve etkileşim. Klavye eşdeğerleri: WASD/oklar, J veya ekrandaki saldırı düğmesine basılı tutma, Q/E yetenek, Space/Shift atılma, F etkileşim; I/C/T paneller.
- **Adalet:** Kül kurdu kısa bir saldırı halkası/telegraph gösterir. Oyuncu saldırıyı zamanında atılmayla boşa çıkarabilir. İri düşman daha yavaş, daha sert vurur. Can sıfırda alana geri dönüş ve temel altın kaybı vardır.
- **Kaynak:** Kor Alevi (hedefli alan hasarı) ve Kül Patlaması (yakın alan kontrolü) öz tüketir; öz zamanla yavaşça yenilenir. Yeteneği otomatik kullanan sistem yoktur.
- **Erişilebilir hedefleme:** Temel saldırı, saldırı alanındaki en yakın düşmana yönelir; oyuncu saldırıyı yine kendisi başlatır. Yetenek hedefi mevcut yön veya yakın düşmandır.

## Meta ilerleme ve ekonomi

- **Seviye / XP:** Düşman ve küçük av görevleri XP verir. Seviye; can ve temel hasar artışı, ayrıca yetenek puanı sağlar.
- **Ustalık:** Kısa Kılıç, Kor Alevi ve Kül Patlaması ayrı sayaç tutar. Kullanım eşiklerinde ilgili eylemin hasarı yükselir. Ustalık yalnızca o eylem aktif kullanıldığında artar.
- **Yetenek ağı (tam oyun hedefi):** 60+ düğümlü, 6 dala ayrılan, çoklu bağlantılı ağ: Silah, Kor, Alan Kontrolü, Hareket, Hayatta Kalma ve Kaynak. Düğümler alternatif yollarla açılır; puan iadesi kamp kaynağı ister. Bu prototipte telefon ekranında rahat test için 6 temsilci düğüm bulunur.
- **Eşya:** Normal / büyülü / nadir / efsanevi nadirlik; taban değer, eşya seviyesi ve 1–4 rastgele ön/son ek. Silah, başlık, gövde, eldiven, çizme, yüzük ve tılsım yuvaları. Eşya karşılaştırması mevcut ve olası değerleri birlikte göstermeli. Prototipte rastgele ad, nadirlik, hasar ve bir örnek ek ile temel toplama/kuşanma döngüsü uygulanır.
- **Zindan hedefli ganimet:** Tam sürümde her bölgenin düşman havuzu, malzeme tablosu ve benzersiz eşya havuzu ayrıdır. Düşük oranlı eşsizler garantili tekrarlarla değil uzun vadeli hedeflerle edinilir; kötü şans koruması yalnızca çok uzun kuru serilerde yumuşak artış sağlar.
- **Üretim / toplama:** Cevher, canavar postu ve kül özü; düşmanlardan, damar noktalarından ve zindan sandıklarından gelir. Tarifler malzeme ve altın ister; dokunmatik menüde tek açık onay adımı kullanılır. Prototipte Kül Döven örnek tarifi vardır.
- **Yan görev:** Kamp NPC'si “5 kül kurdu avla” gibi kısa, tekrar edilebilir bir hedef verir. XP + nadir malzeme/altın vererek ilerleme engellerini yumuşatır, ana anlatı zorunluluğu oluşturmaz.
- **Risk mührü:** İsteğe bağlı Kızıl Öfke düşman gücünü ve ganimet olasılığını artırır; Riskli Keşif ölümde taşınan malzemenin bir kısmını düşürme pahasına nadir ganimet şansını yükseltir. Temel zorluk mührü kapalıyken dengelenir.

## Mobil UI ve dil

Varsayılan arayüz Türkçedir. Sol altta CAN ve ÖZ küreleri, seviye/XP/altın; üstte bölge, mini harita ve erişilebilir çanta/karakter/dövme/yetenek/görev/mühür menüleri; sağ altta ergonomik aktif savaş kümesi bulunur. Büyük basma alanları, pointer capture ile basılı saldırı ve joystick, ekran küçüldükçe ölçeklenen yerleşim kullanılır. Envanter karşılaştırması, eşyanın kuşanma öncesi/sonrası değerini gösterir. Renk tek başına bilgi taşımaz: nadirlik yazıyla da belirtilir.

## Sistem mimarisi

Prototip bağımlılıksız HTML Canvas 2D olarak tek `index.html` içinde çalışır. Tasarımın tam uygulama sınırları:

| Modül | Sorumluluk |
|---|---|
| `InputAdapter` | Dokunmatik joystick/buton, klavye ve erişilebilir alternatifleri aynı oyun komutlarına çevirir. |
| `GameLoop` | Sabit zaman adımı, sahne geçişi, güncelleme ve çizimi ayırır. |
| `CombatSystem` | Oyuncu eylemlerini, maliyetleri, cooldown'ları, telegraph ve çarpışmayı yönetir. Otomatik saldırı API'si yoktur. |
| `Entity/AI` | Veri odaklı düşman istatistikleri ve okunabilir durum makinesi (bekle, yaklaş, telegraph, saldır, toparlan). |
| `Progression` | XP, seviye, beceri ağı ve eylem bazlı ustalık eşiklerini hesaplar. |
| `Loot/RNG` | Bölge tablosu, eşya tabanı, ek havuzları, nadirlik ağırlıkları ve rastgele seed'i yönetir. |
| `Inventory/Crafting` | Yuvalı envanter, karşılaştırma, tarif doğrulama ve malzeme harcamalarını atomik yürütür. |
| `Quest/Risk` | Hafif hedefleri, ödül koşullarını, zindan modifiyerlerini ve ölüm kaybını tanımlar. |
| `HUD/Localization` | Türkçe metin anahtarları, ölçeklenen HUD, mini harita, araç ipucu ve durum göstergeleri. |
| `SaveService` | Sürüm numaralı yerel kayıt; gelecekte bulut senkronizasyonu. Oyun içi ekonomi doğrulaması sunucu otoriter çok oyunculuda sunucuya taşınır. |

Gerçek mobil üretim sürümü bu modülleri test edilebilir TypeScript paketlerine ayırır, deterministic loot seed ve save migration ekler, ekran okuyucu etiketleri / titreşim ayarlarını sunar. Bu dosyadaki prototip oynanış ve arayüz konseptini hemen çalıştırılabilir biçimde gösterir; çevrimdışı, yerel oturumdur ve kalıcı kayıt iddiasında bulunmaz.

## Prototip kontrol listesi

- Aç: `index.html` dosyasını modern mobil veya masaüstü tarayıcıda çalıştır.
- Savaş: hareket et, **SALDIR**'a basılı tut, Q/E becerilerini ve Space atılmasını kullan.
- Ganimet: düşmanları yen; parlayan ganimete yaklaş ve **ETKİLEŞ**'e bas.
- İlerleme: **GÖREV**, **ÇANTA**, **DÖVME**, **YETENEK** ve **MÜHÜR** panellerini dene.
