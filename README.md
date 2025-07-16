# Intrusion Detection with Machine Learning

📊 Anormal Ağ Trafiğinin Tespiti - CICIDS2017

Bu proje, Kanada Siber Güvenlik Enstitüsü (CIC) tarafından yayımlanan CICIDS2017 veri kümesi kullanılarak ağ trafiğinde anomali (saldırı) tespiti için bir makine öğrenmesi modeli geliştirmeyi amaçlar. 

📚 Kaynak<br>
"Makine Öğrenmesi Yöntemleriyle Anormal Ağ Trafiğinin Tespiti" adlı akademik çalışma temel alınmıştır.

Çalışma : https://dergipark.org.tr/tr/pub/dubited/issue/43004/498358

Çalışmada elde edilen sonuçlar : 
![Görsel  1](Images/ForReadMe4.PNG)

Veriseti : https://www.kaggle.com/datasets/chethuhn/network-intrusion-dataset/data

🔍 Amaç

Ağ trafiği kayıtlarından çıkarılan istatistiksel özellikler kullanılarak, normal ve anormal trafiğin (DoS, DDoS, Botnet vb.) sınıflandırılması hedeflenmektedir.

🗂️ Veri Kümesi
CICIDS2017: Gerçek dünya senaryolarında oluşturulmuş ağ trafiği.

78+ özellik içeren .csv dosyaları kullanılmıştır.

Özellikler CICFlowMeter ile ağ trafiğinden çıkarılmıştır.

CICFlowMeter ile ağ trafiğinden özelliklerin nasıl çıkartıldığı ve bu özellikler hakkında detaylı bilgiler Npcap---Network Reposunda paylaşılacaktır.

![Görsel  2 (Görseller ilgili makaleden alınmıştır.)](Images/ForReadMe1.PNG)
![Görsel  3](Images/ForReadMe2.PNG)
![Görsel  4](Images/ForReadMe3.PNG)

⚙️ Kaynak kod

Kayıtlı Modeller: https://drive.google.com/drive/folders/12P2nE41sQqBLIzCJvWrwcIU0k7Kgit5V?usp=sharing

1. 📁 Veri Yükleme ve Birleştirme
   
Tüm .csv dosyaları okunur ve tek bir DataFrame'de birleştirilir.

3. 🧹 Veri Temizleme
   
Eksik değerler ve inf değerler kontrol edilip temizlenir.

Yinelenen satırlar kaldırılır.

Boşluk içeren sütun isimleri düzeltildi.

3. 📈 Veri Analizi
   
Saldırı türlerinin dağılımı görselleştirildi.

Flow Bytes/s gibi bazı değişkenlerin istatistikleri farklı saldırı türleri için incelendi.

4. 🧪 Özellik Seçimi
   
Varyansı 0 olan özellikler çıkarıldı.

Aynı olan sütunlar (ör. Total Fwd Packets = Subflow Fwd Packets) silindi.

Korelasyonu yüksek (> 0.9) olan sütunlar tespit edildi.

7. ⚗️ PCA (Principal Component Analysis)
   
Korelasyonu yüksek bazı sütunlar PCA ile birleştirildi (ör: Bwd Packet Length Max, Mean, Std).

5. 🧠 Model Eğitimi
   
Random Forest ve Decision Tree modelleri eğitildi.

Verinin %70'i eğitim, %30'u test için kullanıldı.

Performans classification_report ile ölçüldü.

6. 📉 Özellik Önem Değerlendirmesi
   
En etkili 20 özellik görselleştirildi.

8. 💾 Model Kaydetme
   
Eğitim tamamlanan Random Forest ve Decision Tree Classifier modeli rf_model.pkl ve dt_model.pkl olarak kaydedildi.

🧪 Kullanılan Kütüphaneler

pandas, numpy, matplotlib, seaborn

sklearn (RandomForestClassifier, DecisionTreeClassifier, PCA, train_test_split)

joblib

📌 Notlar

Ölçekleme (StandardScaler) bazı modeller için önerilir (SVM, KNN), ancak bu proje temel modellerle başlamıştır.

Geliştirme için CUDA destekli modeller (XGBoost GPU) ileride entegre edilebilir.
