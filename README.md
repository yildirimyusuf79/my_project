# Turkish Lira Banknote Classification Project

## Giriş
Bu projede, **Türk Lirası banknotlarının sınıflandırılması** üzerine bir makine öğrenmesi çalışması yapılmıştır. Çalışmada Kaggle'da yer alan **Turkish Lira Banknote Dataset** kullanılmıştır. Dataset farklı banknot değerlerinden oluşan görüntüler içermektedir: `5`, `10`, `20`, `50`, `100`, `200`.

Projede amaç, derin öğrenme modelleri kullanarak banknotların doğru sınıflandırılmasını sağlamaktır. Modelin eğitiminde veri artırma (data augmentation), dropout ve diğer regularization yöntemleri kullanılmış, overfitting riski minimize edilmeye çalışılmıştır.

## Kullanılan Yöntemler
- **Veri Ön İşleme:** Görüntüler yeniden boyutlandırıldı ve normalizasyon uygulandı.  
- **Model Mimarisi:** CNN (Convolutional Neural Network) tabanlı bir model kullanıldı. Katman sayısı, filtre sayıları, kernel boyutları ve dense layer boyutları hiperparametre optimizasyonu ile belirlendi.  
- **Hiperparametre Optimizasyonu:** Learning rate, batch size, optimizer seçimi ve dropout oranları farklı kombinasyonlarla denenmiştir.  
- **Model İzleme:** Eğitim ve doğrulama kayıpları ile doğruluk değerleri grafiklerle takip edildi. TensorBoard veya W&B (isteğe bağlı) kullanılarak modelin performansı görselleştirildi.  
- **Görselleştirme:** Grad-CAM ve Eigen-CAM yöntemleri ile modelin hangi bölgeleri dikkate alarak sınıflandırma yaptığı analiz edilmiştir.  

## Sonuçlar
Model, test verisinde yüksek doğruluk göstermiştir. Overfitting/underfitting durumları görsellerle notebook içinde detaylı olarak incelenmiştir.  

## Dosya İçeriği
- `notebook.ipynb` : Modelin eğitim ve değerlendirme süreci, görselleştirmeler.  
- `README.md` : Projenin kısa tanıtımı ve açıklaması.  

---

Proje, Türk Lirası banknotlarını sınıflandırmak ve derin öğrenme yöntemlerini uygulamak isteyenler için örnek teşkil etmektedir.


## Metrikler ve Sonuçlar

Modelin performansı çeşitli metriklerle değerlendirilmiştir:

- **Doğruluk (Accuracy):** Model, eğitim ve doğrulama setlerinde yüksek doğruluk göstermiştir. Örneğin, validation setinde %X doğruluk elde edilmiştir.  
- **Loss (Kayıp):** Eğitim sırasında modelin kayıp değeri (loss) düzenli olarak düşmüş ve validation loss ile büyük bir fark gözlenmemiştir, bu da overfitting riskinin minimal olduğunu göstermektedir.  
- **Confusion Matrix:** Sınıflar arasındaki yanlış sınıflandırmalar incelenmiş ve modelin çoğunlukla yüksek değerli banknotları doğru ayırt ettiği görülmüştür.  

### Yorumlar
- Model, banknotların sınıflandırılmasında özellikle yüksek değerdeki banknotlarda güçlü performans göstermektedir.  
- Grad-CAM ve Eigen-CAM görselleştirmeleri, modelin sınıflandırma yaparken hangi bölgeleri dikkate aldığını göstermiştir; genellikle banknot üzerindeki rakam ve desenler önemli etkenler olarak öne çıkmıştır.  
- Hiperparametre optimizasyonu (katman sayısı, filtre boyutu, dropout oranı, learning rate) sayesinde overfitting minimize edilmiş, model hem eğitim hem de doğrulama setinde dengeli bir performans göstermiştir.  
- Kullanılan optimizer ve batch size gibi parametreler performansı etkileyen kritik faktörlerdir ve deneysel olarak belirlenmiştir.  

Bu çalışma, sadece kod yazmakla kalmayıp, modeli anlamak, çıktıları yorumlamak ve görselleştirmeler ile desteklemek üzerine odaklanmıştır. Bu nedenle elde edilen sonuçlar modelin sınıflandırma mantığını ve karar verme süreçlerini açıklayacak şekilde yorumlanmıştır.



## Ekler

Projemiz kapsamında bazı ekstra çalışmalar da gerçekleştirilmiştir:

- **Deployment:** Modelin kullanımını kolaylaştırmak amacıyla bir **UI** klasörü eklenmiştir. Bu klasörde, Streamlit tabanlı örnek bir uygulama scripti bulunmaktadır. Bu sayede kullanıcılar, eğitimli modeli kendi verileri üzerinde hızlıca test edebilirler.  

- **End-to-End GPU Kullanımı:** Modelin eğitim ve çıkarım süreçlerinde GPU kullanımı sağlanmıştır. Bu sayede büyük veri setleri ve yüksek çözünürlüklü görsellerle yapılan işlemler hızlı ve verimli bir şekilde gerçekleştirilmiştir.  

- **Notebooks:** Repoda bulunan supervised ve unsupervised notebooklar, model eğitimi, hiperparametre optimizasyonu ve görselleştirme adımlarını kapsamlı şekilde içermektedir. Ek bir notebook deploy amaçlı kullanılmaktadır, fakat temel çalışma notebooklar ile paralel şekilde yürütülmektedir.



## Sonuç ve Gelecek Çalışmalar

Bu proje kapsamında, Türk Lirası banknot veri seti kullanılarak bir görüntü sınıflandırma modeli geliştirilmiştir. Model, Conv2D tabanlı bir derin öğrenme mimarisi ile eğitilmiş, hiperparametre optimizasyonu ve overfitting kontrolü sağlanmıştır. Grad-CAM ve Eigen-CAM gibi yöntemlerle modelin hangi bölgeleri dikkate aldığı görselleştirilmiştir.  

**Gelecek çalışmalar için öneriler:**

- **Arayüz geliştirme:** Kullanıcıların modeli kolayca test edebilmesi için Streamlit veya başka bir UI framework’ü ile web arayüzü eklenebilir.  
- **Gerçek zamanlı veri toplama:** Model, kameradan gelen görüntülerle anlık sınıflandırma yapacak şekilde güncellenebilir.  
- **Veri setinin genişletilmesi:** Daha fazla banknot ve farklı ışık/konum koşulları eklenerek modelin genelleme kapasitesi artırılabilir.  
- **Yeni teknolojiler:** Transfer learning, self-supervised learning ve ileri görsel açıklama teknikleri ile modelin performansı iyileştirilebilir.  
- **Kariyer açısından:** Bu proje, bilgisayarlı görü ve derin öğrenme alanında yetkinliğinizi gösteren bir portföy çalışması olarak kullanılabilir. Gelecekte yapay zekinin finans, güvenlik ve görsel tanıma uygulamalarına yönelik projelere geçiş için temel oluşturur.


Linkler
https://www.kaggle.com/code/yildirimyusuf79/notebookd020a4569c/edit/run/263808670
