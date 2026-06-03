🍷 Wine Reviews - NLP & Multi-Input Deep Learning Price Prediction
📌 Proje Hakkında

Bu projede Wine Reviews veri seti kullanılarak şarap fiyatlarının tahmin edilmesi amaçlanmıştır.

Çalışma kapsamında üç farklı yaklaşım uygulanmıştır:

NLP tabanlı metin modeli
Tabular (sayısal + kategorik) veri modeli
NLP ve tabular verilerin birleştirildiği Multi-Input Neural Network modeli

Amaç, şarap açıklamalarından (wine descriptions) ve diğer özelliklerden yararlanarak şişe fiyatını tahmin etmektir.

📊 Veri Seti

Kaynak:

https://www.kaggle.com/datasets/zynicide/wine-reviews

Kullanılan dosya:

winemag-data-130k-v2.csv

Başlangıç veri boyutu:

129,971 satır
13 sütun

Eksik değerler temizlendikten sonra:

22,387 satır
13 sütun
📋 Kullanılan Değişkenler
Metinsel Veri
description

Şarap tadım notları ve açıklamaları.

Örnek:

"Aromas include tropical fruit, broom, brimstone..."
Sayısal ve Kategorik Veriler
points
region_2

Target değişken:

price
🔍 Veri Ön İşleme
Metin İşleme
Tokenization
Kelimelere ayırma
Vocabulary oluşturma
Padding

Vocabulary Boyutu:

16,075 kelime

Padding Uzunluğu:

60
Kategorik Veri İşleme

One-Hot Encoding uygulanmıştır:

OneHotEncoder()

Kullanılan sütun:

region_2
Sayısal Veri İşleme

Standardizasyon uygulanmıştır:

StandardScaler()

Kullanılan sütun:

points
🧠 Model 1 - NLP Modeli

Mimari:

Input
↓
Embedding (40)
↓
Conv1D
↓
Conv1D
↓
Flatten
↓
Dense(30)
↓
Dropout
↓
Dense(1)

Toplam Parametre:

668,121

Kayıp Fonksiyonu:

MSE

Optimizasyon:

Adam

Değerlendirme Metrikleri:

MAE
🧠 Model 2 - Tabular Veri Modeli

Girdiler:

Points
Region_2

Mimari:

Input
↓
Dense(64)
↓
Dense(32)
↓
Dense(1)

Toplam Parametre:

3,329
🧠 Model 3 - Multi-Input Neural Network

İki modelin çıktıları birleştirilmiştir.

Wine Description
↓
NLP Model
↓
Output 1
          \
           \
            → Concatenate
           /
          /
Tabular Model
↓
Output 2

↓
Dense(10)
↓
Dense(1)

Toplam Parametre:

671,491
📈 Sonuçlar
Baseline

Her zaman ortalama fiyatı tahmin eden model:

MAE ≈ 17.73 $
NLP Model

Validation MAE:

≈ 14.10 $
Tabular Model

Validation MAE:

≈ 13.92 $
Multi-Input Model

Validation MAE:

≈ 13.00 $
🎯 Çıkarımlar
Şarap açıklamaları fiyat hakkında önemli bilgiler içermektedir.
Bölge ve puan bilgileri fiyat tahminini iyileştirmektedir.
Farklı veri kaynaklarının birleştirilmesi model performansını artırmıştır.
Multi-Input Neural Network yaklaşımı tek başına NLP veya tabular modellerden daha başarılı sonuç vermiştir.
🛠 Kullanılan Teknolojiler
Python
Pandas
NumPy
TensorFlow / Keras
Scikit-Learn
Matplotlib
Seaborn
🚀 Öğrenilen Konular

Bu proje kapsamında:

NLP temel işleme adımları
Tokenization
Padding
Embedding Katmanları
Conv1D ile metin analizi
One-Hot Encoding
Feature Scaling
Functional API
Multi-Input Neural Networks
Regression Problemleri
Deep Learning Model Birleştirme

konularında uygulamalı deneyim kazanılmıştır.

👤 Author

Doruk Pamir

GitHub: https://github.com/DPAMIR8781
LinkedIn: www.linkedin.com/in/doruk-pamir

Bu README, Workintech Data Science & AI Programı kapsamında gerçekleştirilen Wine Reviews NLP ve Multi-Input Deep Learning çalışması için hazırlanmıştır.
