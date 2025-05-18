# DenseNet121 ile Diyabetik Retinopati Sınıflandırması

Bu proje, **Diabetic Retinopathy 2015 Colored Resized** veri kümesi kullanılarak diyabetik retinopati evrelerinin sınıflandırılmasını hedeflemektedir. Görüntü işleme teknikleri ve transfer learning yöntemi ile model eğitimi gerçekleştirilmiştir.

Kullanılan sınıflar:
- Mild
- Moderate
- Severe
- Proliferate_DR
- No_DR

---

## 🎯 Proje Hedefleri

- Görsel veriler üzerinde gelişmiş ön işleme adımlarını uygulamak
- DenseNet121 mimarisi ile transfer learning kullanmak
- Hem orijinal hem işlenmiş veriler üzerinde model başarımını karşılaştırmak
- HSV uzayında özgün bir parlaklık ve doygunluk artırıcı fonksiyon geliştirmek

---

## 🧪 Görüntü İşleme Adımları

Her bir görüntüye aşağıdaki adımlar sırasıyla uygulanmıştır:

1. **R ve G Kanallarının Ayrılması** – Mavi kanal sıfırlanır.
2. **CLAHE ile Kontrast Artırımı** – Gri tonlamalı görüntüde uygulanır.
3. **Keskinleştirme (Sharpening)** – Özel bir filtre çekirdeği kullanılır.
4. **Gaussian Blur** – Arka plan bulanıklaştırılır.
5. **Canny Kenar Tespiti** – Görseldeki kenar yapılarını tespit eder.
6. **Dilatasyon** – Kenar kalınlıkları artırılır.
7. **Bitwise İşlemi** – Keskinleştirilmiş ve bulanık görüntüler birleştirilir.
8. **Kırmızı Kenar Vurgusu** – Kenarlar kırmızı renkte öne çıkarılır.
9. **Final Görüntü Oluşturma** – İşlenmiş görüntüler birleştirilir.
10. **Parlaklık ve Doygunluk Artırma** – HSV uzayında özgün bir fonksiyon uygulanır.

> Görsel işleme süreci ikiye bölünmüş akış diyagramı ile gösterilmiştir.

---

## 🤖 Transfer Learning ile Eğitim

- **Model:** DenseNet121 (ImageNet ağırlıkları ile)
- **Yöntem:** Fine-tuning (ince ayar)
- **Strateji:** EarlyStopping uygulanmıştır (5 epoch boyunca validation loss iyileşmezse durur)

Model, hem orijinal hem işlenmiş veri setiyle eğitilerek performans karşılaştırması yapılmıştır.

---

## 📈 Performans Karşılaştırma Tablosu

| Ölçüt                 | Orijinal Veri | İşlenmiş Veri |
|-----------------------|---------------|----------------|
| Doğruluk (Accuracy)    | 38.0          | 34.0           |
| Duyarlılık (Recall)    | 38.0          | 34.0           |
| Özgüllük (Specificity) | 86.6          | 83.6           |
| Kesinlik (Precision)   | 37.0          | 35.0           |
| F1-Score               | 37.0          | 34.0           |

> Bu sonuçlara göre işlenmiş veri ile model başarımında küçük bir düşüş gözlemlense de, geliştirme ve genelleme potansiyeli bulunmaktadır.

---

## 🛠️ Kullanılan Teknolojiler

- Python
- OpenCV
- TensorFlow / Keras
- DenseNet121 (Transfer Learning)
- Matplotlib, Seaborn

---

## ✍️ Geliştirici

**İrem Kabaoğlu**  
`Sakarya Üniversitesi - Bilişim Sistemleri Mühendisliği`  
`ISE456 - Bilgisayar Görmesine Giriş`
