# Türkçe Metin Sınıflandırma Projesi

Bu proje, Türkçe metin verileri için sınıflandırma modelleri geliştirmeyi amaçlamaktadır. Haber makalelerini önceden tanımlanmış kategorilere yüksek doğruluk oranıyla sınıflandırmak için çeşitli makine öğrenmesi ve derin öğrenme yöntemleri ile transformer modelleri kullanılmıştır.

## Genel Bakış

Bu çalışma, **[TTC4900 veri seti](https://www.kaggle.com/datasets/savasy/ttc4900)** kullanılarak metin sınıflandırma tekniklerini araştırmaktadır. Ana adımlar şunlardır:

1. **Özellik Çıkarımı**: Bag of Words (BoW), TF-IDF ve Word2Vec kullanılarak özellikler çıkarılmıştır.
2. **Makine Öğrenmesi Modelleri**: Random Forest, XGBoost, LightGBM, SVM ve ANN uygulanmıştır.
3. **Derin Öğrenme Modelleri**: CNN, LSTM, BiLSTM ve GRU gibi ileri düzey mimariler incelenmiştir.
4. **Transformer Modelleri**: Türkçe metin sınıflandırma için BERT tabanlı modeller özelleştirilmiştir.


## Veri Seti Hazırlama ve Temizleme

`7allV03.csv` dosyası üzerinde şu adımlar uygulanarak ön işlemler yapılmıştır:

1. **Çift veri satırlarının kaldırılması**
2. **Kısaltmaların düzeltilmesi** ("AA" örneğin "Anadolu Ajansı" olarak değiştirilmiştir)
3. **Metin temizleme**:
   - Küçük harfe dönüştürme
   - URL'lerin, e-posta adreslerinin, sayıların, noktalama işaretlerinin, emojilerin ve nadir kelimelerin kaldırılması
   - Türkçe durak kelimelerinin (stopwords) temizlenmesi

**Kök Bulma ve Lemmatizasyon** işlemleri şu araçlarla yapılmıştır:

- **Zemberek**: Morfolojik özellikleri analiz ederek kelimeleri kök hallerine indirmiştir.
- **Stanza**: Kelimelerin anlamlarına uygun temel formlarını sağlamıştır.

### Veri Seti Kategorileri

Temizlenen veri seti şu kategorileri içermektedir:

- Ekonomi: 690 örnek
- Politika: 690 örnek
- Dünya: 676 örnek
- Teknoloji: 649 örnek
- Spor: 635 örnek
- Sağlık: 631 örnek
- Kültür: 567 örnek


## Modeller ve Sonuçlar

### Makine Öğrenmesi Modelleri

- **En İyi Performans**:
  - Özellik: TF-IDF
  - Model: SVM
  - F1 Skoru: 0.8946
  - Doğruluk: 0.8943

### Derin Öğrenme Modelleri

#### ANN

- **En İyi Performans**:
  - Özellik: BoW
  - F1 Skoru: 0.9106
  - Doğruluk: 0.9108

#### CNN, LSTM, BiLSTM, GRU

- **En İyi Performans**:
  - Model: CNN + BiLSTM (Rastgele Başlatma)
  - Doğruluk: 0.8711

### Transformer Modelleri

| Model                                       | Doğruluk (K-Fold) |
| ------------------------------------------- | ----------------- |
| **savasy/bert-turkish-text-classification** | 0.98204           |
| bert-base-multilingual-uncased              | 0.95408           |


## Değerlendirme Metrikleri

Tüm modeller şu metriklerle değerlendirilmiştir:

- Kesinlik (Precision)
- Duyarlılık (Recall)
- F1 Skoru
- Doğruluk
- AUC (ROC E- AUC (ROC E\u011risi)
- Karmaşıklık Matrisi


## Kurulum ve Kullanım

### Gereksinimler

- Python 3.x
- Kütüphaneler: `pandas`, `scikit-learn`, `tensorflow`, `statsmodels`, `zemberek-python`, `stanza`, `xgboost`, `lightgbm`

## Proje Öne Çıkanları

- **Zemberek** ve **Stanza** gibi Türkçeye özel araçlarla ön işlemler.
- Klasik makine öğrenmesi, derin öğrenme ve transformer tabanlı modellerin kapsam lı karşılaştırması.
- **savasy/bert-turkish-text-classification** modelinin K-Fold doğruluk oranı ile zirve performans (0.98204).


## Teşekkürler

TTC4900 veri setinin oluşturucularına ve Zemberek ile Stanza kütüphanelerinin katkıcılarına teşekkür ederiz.

