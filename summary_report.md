# [TR]
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

#[Eng.]
# Thorium-232 Decay Statistical Modeling — Educational Report

**This report is entirely for educational purposes; it contains no real nuclear production or operational information.**

---

## 1. Data Summary

- Number of rows: **500**  
- Columns: `t`, `counts`, `true_signal`, `background`, `is_injected_anomaly`

---

## 2. Model Comparison (GLM)

| Model | AIC | BIC |
|:------|:----:|:----:|
| Poisson | 6713.82 | 758.09 |
| Negative Binomial | 4965.90 | -3022.10 |

The Negative Binomial model is more appropriate than Poisson in cases of **overdispersion**.  
**Decision:** Because Deviance/Df ≫ 1, the **Negative Binomial** model was chosen.  
(Lower AIC/BIC and adjusted standard errors were observed.)

---

## 3. Selected Model — Detailed Results (Negative Binomial)

| Variable | Coefficient (log-rate) | P-value | Comment |
|:---------|:----------------------:|:-------:|:--------|
| `true_signal` | 0.0122 | 0.000 | Significant (Positive effect) |
| `background`  | -0.0119 | 0.880 | Not significant |

**Interpretation:**  
In the Negative Binomial model, the `true_signal` variable is **statistically significant** and has a positive effect (P < 0.001).  
The `background` variable, which appeared borderline significant in the Poisson model, is **not significant** in the NB model after adjusted standard errors (P ≈ 0.880).

---

## 4. Bootstrap Uncertainty

- Median of counts (bootstrap, 95% CI): **42.99** [40.00, 46.00]  
- Number of bootstrap samples (n): **2000**

---

## 5. Anomaly Detection

- Method used: **Isolation Forest + Z-score** combined approach  
- Number of detected anomalies: **20**  
- Estimated precision: **0.05**, recall: **0.05**

---

## 6. Ethics and Limitations

- This work uses **synthetic data** and **statistical / computational methods** only.  
- It contains **no operational information** for producing or applying real nuclear processes.  
- The purpose is to **teach and develop data science skills**.

---

## 7. Long-Term Goal (Educational / Theoretical)

Without performing any real-world production or experimental application, the goal is to develop statistical and computational models of decay chains akin to Thorium → Protactinium → Uranium, and to analyze the **time-series patterns** of such processes using data-science techniques.
