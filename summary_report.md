# Toryum 232 Dönüşümünün İstatistiksel Modellemesi — Eğitim Raporu


**Bu rapor tamamen eğitim amaçlıdır; gerçek nükleer üretim/operasyon bilgisi içermez.**

## 1. Veri Özeti


Satır sayısı: **500**

Sütunlar: `t`, `counts`, `true_signal`, `background`, `is_injected_anomaly`.

## 2. Modellerin Karşılaştırması (GLM)


- **Poisson** AIC: 6713.82, BIC: 758.0885625852757
- **Negatif Binomial** AIC: 4965.90, BIC: -3022.1047684768787

Genellikle overdispersiyon durumlarında Negatif Binomial, Poisson’a göre daha iyi uyum sağlar (AIC/BIC karşılaştır).
**Karar:** Aşırı yayılım (overdispersion) tespit edildiği için ($	ext{Deviance}/	ext{Df} \gg 1$) **Negatif Binomial** modeli seçilmiştir. (Daha düşük $	ext{AIC}/	ext{BIC}$ ve düzeltilmiş standart hatalar).

## 3. Seçilen Modelin Detaylı Sonuçları (Negatif Binomial)


| Değişken | Katsayı (Log-Oran) | $P$-Değeri | Yorum |

| :--- | :---: | :---: | :--- |

| `true_signal` | 0.0122 | 0.000 | Anlamlı (Pozitif Etki) |

| `background` | -0.0119 | 0.880 | Anlamsız |


**Yorum:** Negatif Binomial modelinde `true_signal` değişkeni **istatistiksel olarak anlamlı** ve pozitif etkilidir ($P<0.001$). $	ext{Poisson}$ modelinde sınırda anlamlı görünen `background` değişkeni ise ($	ext{NB}$ modelinin düzeltilmiş standart hataları ile) **anlamsız** bulunmuştur ($P \approx 0.880$).

## 4. Bootstrap Belirsizlik


Counts medyanı (bootstrap, 95% CI): **42.99** [40.00, 46.00] (n=2000).
## 5. Anomali Tespiti


IsolationForest + Z-score birleşik anomali sayısı: **20**.
Tahmini precision (GT'e göre): **0.05**, recall: **0.05**.
## 6. Etik ve Sınırlar


- Bu çalışma yalnızca **sentetik veriler** ve **istatistiksel/hesaplamalı** yöntemlerle yürütülmüştür.
- Gerçek nükleer süreçleri üretmeye/uygulamaya yönelik **hiçbir operasyonel bilgi** içermez.
- Amaç, eğitim ve veri bilimi becerilerini geliştirmektir.

## 7. Uzun Vadeli Hedef (Eğitimsel/Teorik)


Gerçek dünyada herhangi bir üretim veya deneysel uygulama gerçekleştirmeksizin,
toryum–protaktinyum–uranyum benzeri dönüşüm zincirlerinin istatistiksel ve hesaplamalı
modellerini geliştirmek, bu süreçlerin ölçümsel imzalarını (zaman serisi kalıpları) veri bilimi
teknikleriyle karakterize edebilmek.
