# E-Commerce-Sentiment-Analysis-XGBoost

#  Yapılandırılmış ve Yapılandırılmamış Veri Harmanlaması ile Kozmetik Ürün Başarı Tahmini ve Kar Optimizasyonu 

[![GitHub License](https://img.shields.io/badge/Academic-Project-blue.svg)](https://github.com/)
[![Python](https://img.shields.io/badge/Python-3.13-brightgreen.svg)](https://python.org)
[![XGBoost](https://img.shields.io/badge/Model-XGBoost-orange.svg)](https://xgboost.readthedocs.io/)

Bu proje, e-ticaret kozmetik (fondöten) dikeyinde faaliyet gösteren bir işletmenin envanter yönetim süreçlerini optimize etmek amacıyla geliştirilmiş üst düzey bir **Yönetim Bilişim Sistemleri (YBS)** ve Veri Bilimi projesidir. Proje, teknik yapay zeka başarılarını doğrudan işletme diline (Türk Lirası ve ROI) dönüştürerek proaktif karar destek mekanizmaları sunar.

---

##  İş Problemi ve Motivasyon
Modern e-ticarette yanlış envanter stoklamanın firmalara yüklediği operasyonel, depolama ve finansal maliyet (ölü stok zararları) oldukça yüksektir. Geleneksel yaklaşımlar yalnızca yapılandırılmış (fiyat, kategori) verileri incelerken; bu çalışmada tüketicilerin dijital dünyada bıraktığı yapılandırılmamış metin verileri (müşteri yorumları) NLP ile analiz edilerek sisteme entegre edilmiştir. Amaç, kara kutu modelleri şeffaflaştırarak firmaya maksimum kârlılık sağlamaktır.

---

##  Proje Mimarisi & Öne Çıkan Özellikler

### 1. Veri Harmanlama 
Projede tek bir hazır veri seti kullanılmamış, iki farklı kaynaktan gelen heterojen yapılar esnek bir mimariyle evlendirilmiştir:
* **Yapılandırılmamış Veri:** Trendyol platformu üzerinden kazınan (scraping) **11.128 adet** gerçek müşteri yorumu ve puanı (CSV).
* **Yapılandırılmış Veri:** Sektörel ürün detaylarını, marka kırılımlarını ve fiyatlarını barındıran JSON pazar dosyaları.

### 2. İş Mantığına Dayalı Özellik Mühendisliği (Business-Driven Feature Engineering)
Sistem performansını mutlaklaştırmak adına ham verilerden işletme mantığına uygun **3 özgün öznitelik** türetilmiştir:
* **Ortalama Duygu Skoru (Sentiment Score):** NLP teknikleriyle müşteri yorum metinlerinin $[-1, +1]$ arasında sayısal mutluluk skoruna dönüştürülmesi.
* **Fiyat / Performans (F/P) Endeksi (`fp_endeksi`):** Müşteri tatmini ile birim fiyatı harmanlayan projenin kalbi niteliğindeki iş zekası metriği.
* **Marka Popülarite Oranı:** Markaların platform üzerindeki pazar penetrasyonu ve etkileşim ağırlığı.

---

##  Modelleme ve Açıklanabilir Yapay Zeka (XAI)
* **Algoritma:** Yüksek performans ve kararlılık sunan envanter odaklı **XGBoost Classifier** modeli tercih edilmiştir.
* **Teknik Başarı:** Model, test seti üzerinde **1.00 (Kusursuz) F1-Score ve Accuracy** üretmiştir.
* **SHAP Analizi (Kara Kutunun Açılması):** Modelin kararlarını şeffaflaştırmak adına SHAP analizi uygulanmıştır. Çıkan bulgulara göre, modelin bir ürünün başarısını tahmin ederken en yüksek ağırlığı (`importance`) bizim kurguladığımız **F/P Endeksi** değişkenine verdiği ispatlanmıştır.

---

##  İş Senaryosu ve Finansal Simülasyon (ROI Analizi)
Modelin başarısı teorik metriklerle sınırlı bırakılmamış, kuruma sağladığı net finansal katma değer maliyet matrisi üzerinden hesaplanmıştır:

* **Geleneksel Yöntem (Yapay Zekasız):** Şirket körlemesine stoklama yapsaydı satmayan 201 riskli üründen dolayı **20.100 TL net ölü stok zararına** uğrayacak ve net dönem kârı **384.900,00 TL** olacaktı.
* **YBS Yapay Zeka Modeli (Önerilen):** Riskli ürünlerin sipariş aşamasında engellenmesiyle ölü stok maliyeti **0.00 TL'ye düşürülmüş**, şirket net kârı **405.000,00 TL** seviyesine çıkarılmıştır.

> **Stratejik ROI Çıktısı:** Modelin şirkete sağladığı net finansal katma değer **20.100,00 TL**'dir. Sadece bu yapay zeka modelinin devreye alınması, şirketin net dönem kârlılığını durduğu yerde **%5.22 artırmıştır (Yatırım Getirisi - ROI)**.

---

##  Klasör Yapısı
```text
📁 E-Commerce-Sentiment-Analysis-XGBoost
 │-- 📄 final.ipynb               # Veri önişleme, NLP, modelleme ve XAI kodları
 │-- 📄 fondotenler_yorumlari.csv  # Trendyol'dan çekilen müşteri yorum verisi
 │-- 📄 Yonetici_Ozeti_Raporu.pdf  # İş senaryosu ve finansal ROI'yi içeren resmi rapor dökümanı
 │-- 📄 image_8acb84.png           # Modelin SHAP açıklanabilirlik grafiği görseli
 │-- 📁 json_data/                 # Ürün detaylarını barındıran kaynak pazar dosyaları
Data Fusion, NLP Sentiment Analysis, XGBoost and ROI Simulation project for E-commerce
