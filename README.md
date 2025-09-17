# Spor Salonu Yoğunluk Tahmini (Gym Crowdedness Prediction)

Bu proje bir spor salonundaki insan sayısını çeşitli metriklere (zaman, hava durumu, akademik takvim vb.) göre tahmin etmeyi amaçlayan bir makine öğrenmesi modeli oluşturmayı amaçlamaktadır. Veri ön işleme (data preprocessing), keşifsel veri analizi (EDA), model karşılaştırması ve hiperparametre optimizasyonu (hyperparameter tuning) gibi adımları içerir.

## 📊 Proje Hakkında

Projede `gym_crowdedness.csv` veri setini kullanarak (verisetini incelemek isterseniz [bu linkten](https://www.kaggle.com/datasets/nsrose7224/crowdedness-at-the-campus-gym) ulaşabilirsiniz) spor salonunun belirli bir zamanda kaç insanın bulunacağını tahmin eden regresyon modelleri geliştirmeyi amaçladım.

Projeyi aşağıdaki adımları izleyerek geliştirdim:
- **Veri Temizleme ve Özellik Mühendisliği (FE):** Zaman verisinin içerisinden yıl, ay, saat gibi verileri ayırdım.
- **Keşifsel Veri Analizi (EDA):** Veri setindeki özelliklerin dağılımlarını ve birbirleriyle olan ilişkilerini anlamak için çeşitli grafikler çizerek görselleştirme yaptım.
- **Model Karşılaştırması:** Linear Regression, Lasso, Ridge, K-Neighbors Regressor, Decision Tree Regressor ve Random Forest Regressor gibi farklı regresyon modelleri eğiterek ve performanslarını karşılaştırdım.
- **Hiperparametre Optimizasyonu:** Bu veri setinde en iyi performansı veren iki model (KNN ve RandomForest) için `RandomizedSearchCV` kullandım ve en uygun hiperparametreleri bulmaya çalıştım.

## 💾 Veri Seti

Kullandığım veri seti aşağıdaki özellikleri içermektedir:
- `number_people`: (Hedef Değişken) Spor salonundaki insan sayısı.
- `date` / `timestamp`: Tarih ve zaman bilgisi.
- `day_of_week`: Haftanın günü (0: Pazartesi, 6: Pazar).
- `is_weekend`: Hafta sonu olup olmadığı (1: Evet, 0: Hayır).
- `is_holiday`: Tatil günü olup olmadığı.
- `temperature`: Hava sıcaklığı.
- `is_start_of_semester`: Sömestr başlangıcı olup olmadığı.
- `is_during_semester`: Sömestr dönemi içinde olup olmadığı.
- `month`: Ay.
- `hour`: Saat.

## 🛠️ Kurulum

Projeyi kendi bilgisayarınızda çalıştırmak isterseniz:

1.  **Repository'yi Klonlayın:**
    ```bash
    git clone [https://github.com/emregergin/gym-crowdness-prediction](https://github.com/emregergin/gym-crowdness-prediction)
    cd gym-crowdness-prediction
    ```

2.  **Gerekli Kütüphaneleri Yükleyin:**
    Projede kullanılan kütüphaneleri `requirements.txt` dosyası aracılığıyla kolayca yükleyebilirsiniz.
    ```bash
    pip install -r requirements.txt
    ```
    - `numpy`
    - `pandas`
    - `matplotlib`
    - `seaborn`
    - `scikit-learn`

## 🚀 Kullanım

Projenin tüm adımlarını ve analizleri görmek için `gym_crowdness.ipynb` adlı Jupyter Notebook dosyasında hücreleri teker teker çalıştırabilirsiniz.

## 📈 Sonuçlar

Yaptığım model karşılaştırması sonucunda **Random Forest Regressor** ve **K-Nearest Neighbors Regressor** modellerinin test verisi üzerinde en yüksek performansı (R² skoru > 0.90) gösterdiğini gözlemledim. Bu iki model spor salonu yoğunluğunu yüksek bir doğruluk (accuracy) ile tahmin edebilmektedir. Özellikle saat, hafta sonu durumu ve sömestr dönemi gibi özelliklerin de insan sayısı ile yüksek korelasyona sahip olduğunu doğrulamış oldum. En son olarak ise en iyi parametrelere göre modeli tekrardan çalıştırıp tahminlerdeki değişiklikleri incelemeye çalıştım.
