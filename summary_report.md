# Toryum-232 Dönüşümünün İstatistiksel Modellemesi — Eğitim Raporu

**Bu rapor tamamen eğitim amaçlıdır; gerçek nükleer üretim veya operasyon bilgisi içermez.**

---

## 1. Veri Özeti

- Satır sayısı: **500**  
- Sütunlar: `t`, `counts`, `true_signal`, `background`, `is_injected_anomaly`

---

## 2. Modellerin Karşılaştırması (GLM)

| Model | AIC | BIC |
|:------|:----:|:----:|
| Poisson | 6713.82 | 758.09 |
| Negatif Binomial | 4965.90 | -3022.10 |

Negatif Binomial modeli, **overdispersion (aşırı yayılım)** durumlarında Poisson’a göre daha uygundur.  
**Karar:** Deviance/Df ≫ 1 olduğu için **Negatif Binomial** modeli seçilmiştir.  
(Daha düşük AIC/BIC ve düzeltilmiş standart hatalar gözlenmiştir.)

---

## 3. Seçilen Modelin Detaylı Sonuçları (Negatif Binomial)

| Değişken | Katsayı (Log-Oran) | P-Değeri | Yorum |
|:----------|:------------------:|:---------:|:------|
| `true_signal` | 0.0122 | 0.000 | Anlamlı (Pozitif Etki) |
| `background` | -0.0119 | 0.880 | Anlamsız |

**Yorum:**  
Negatif Binomial modelinde `true_signal` değişkeni **istatistiksel olarak anlamlı** ve pozitif etkilidir (P < 0.001).  
Poisson modelinde sınırda anlamlı görünen `background` değişkeni ise (NB modelinde düzeltilmiş standart hatalarla) **anlamsız** bulunmuştur (P ≈ 0.880).

---

## 4. Bootstrap Belirsizlik

- Counts medyanı (bootstrap, %95 CI): **42.99** [40.00, 46.00]  
- Örnekleme sayısı (n): **2000**

---

## 5. Anomali Tespiti

- Kullanılan yöntem: **Isolation Forest + Z-score** birleşik yaklaşımı  
- Tespit edilen anomali sayısı: **20**  
- Tahmini precision: **0.05**, recall: **0.05**

---

## 6. Etik ve Sınırlar

- Bu çalışma yalnızca **sentetik veriler** ve **istatistiksel / hesaplamalı yöntemler** içermektedir.  
- Gerçek nükleer süreçleri üretmeye veya uygulamaya yönelik **hiçbir operasyonel bilgi** içermez.  
- Amaç, **eğitim ve veri bilimi becerilerini geliştirmektir.**

---

## 7. Uzun Vadeli Hedef (Eğitimsel / Teorik)

Gerçek dünyada herhangi bir üretim veya deneysel uygulama gerçekleştirmeksizin,  
Toryum → Protaktinyum → Uranyum benzeri dönüşüm zincirlerinin **istatistiksel ve hesaplamalı modellerini** geliştirmek,  
ve bu süreçlerin **zaman serisi kalıplarını** veri bilimi teknikleriyle analiz etmektir.
