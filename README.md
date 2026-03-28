# SolarSentinel
### Uzay Havası Erken Uyarı Sistemi

Gerçek zamanlı NOAA ve NASA verileriyle çalışan, yaklaşan jeomanyetik fırtınaları önceden tespit eden açık kaynaklı bir uzay havası izleme panelidir.

---

## Motivasyon

Güneş fırtınaları; GPS sistemlerini bozabilir, yüksek frekanslı radyo iletişimini kesebilir ve elektrik şebekelerinde ciddi dalgalanmalara yol açabilir. Türkiye'nin uzaya yatırımlarını artırdığı bu dönemde, yerli bir erken uyarı altyapısının ne denli kritik olduğu açıktır.

SolarSentinel bu ihtiyaca yanıt vermek için geliştirilmiştir: uydu operatörlerinden amatör gökbilimcilere kadar herkesin anlayabileceği, sade ve erişilebilir bir uzay havası paneli.

---

## Özellikler

**Gerçek Zamanlı İzleme**
- Kp indeksi — jeomanyetik aktivite seviyesi (0–9)
- IMF Bz bileşeni — manyetik alan güney yönlenmesi (fırtına tetikleyicisi)
- Güneş rüzgarı hızı — DSCOVR uydusundan anlık
- Proton yoğunluğu — manyetosfer baskı göstergesi

**Erken Uyarı Motoru**
- G1–G5 skalasına göre otomatik fırtına sınıflandırması
- 24 saatlik jeomanyetik fırtına, radyo kesintisi ve yüksek hız akışı olasılık tahmini
- IMF Bz < −10 nT eşiğinde uyarı sistemi devreye giriyor
- Aurora görünürlük tahmini

**Geçmiş Veri ve Olaylar**
- 7 günlük güneş rüzgarı hızı ve Bz grafiği
- NASA DONKI'dan çekilen son CME, flare ve jeomanyetik fırtına olayları

**Etkilenen Sistemler Analizi**
- GPS/GNSS, yüksek frekanslı radyo, elektrik şebekesi ve aurora için anlık durum değerlendirmesi

---

## Veri Kaynakları

| Kaynak | Veri |
|--------|------|
| NOAA SWPC | Kp indeksi, fırtına tahminleri |
| NASA DSCOVR / ACE | Güneş rüzgarı hızı, IMF Bz, proton yoğunluğu |
| NASA DONKI API | CME, solar flare, GST olay kataloğu |

Tüm veriler açık erişimlidir. API anahtarı gerekmez.

---

## Teknik Yapı

```
SolarSentinelFixed.html   — Tek dosya uygulama (sıfır bağımlılık)
├── Veri katmanı         — Fetch API ile NOAA/NASA uç noktaları
├── Analiz katmanı       — Eşik tabanlı anomali tespiti ve olasılık hesabı
└── Görsel katman        — Chart.js, saf HTML/CSS
```

Harici gereksinimler: yalnızca `Chart.js` (grafik). Sunucu gerekmez, backend gerekmez. Tek HTML dosyası olarak çalışır.

Panel her 5 dakikada otomatik güncellenir.

---

## Kurulum

```bash
git clone https://github.com/SerbayKoc/SolarSentinel.git
cd SolarSentinel
# SolarSentinelFixed.html dosyasını tarayıcıda açın
```

Ya da doğrudan GitHub Pages üzerinden:

```
https://SerbayKoc.github.io/SolarSentinel
```

---

## G-Skalası Referansı

| Seviye | Kp | Etkiler |
|--------|----|---------|
| G1 | ≥5 | Minör — yüksek enlem güç şebekeleri etkilenebilir |
| G2 | ≥6 | Orta — HF radyo bozulması, aurora 55°K'de görünür |
| G3 | ≥7 | Güçlü — GPS degradasyonu, aurora 50°K'de görünür |
| G4 | ≥8 | Şiddetli — yaygın güç sorunları, GPS kaybı |
| G5 | ≥9 | Aşırı — altyapı hasarı riski, aurora 40°K'de görünür |

---

## Kullanılan Teknolojiler

- Saf HTML5, CSS3, JavaScript (ES6+)
- Chart.js — güneş rüzgarı geçmiş grafiği
- NOAA SWPC REST API
- NASA DONKI Web Service API

---

## Geliştirici

**Serbay Koç**

## Araştırmacı

**Kaan Kılıç**

Türkiye Uzay Ajansı Hackathon — 2026  

---

## Lisans

MIT License — açık kaynak, serbestçe kullanılabilir ve geliştirilebilir.
