Seq2Seq (Sequence to Sequence) ifadesinin kısaltmasıdır. İki temel bileşenden oluşur:
- **Encoder (Kodlayıcı):** Giriş dizisini temsil eden bir vektör üretir. Bir cümlenin her bir kelimesini embedding vektörlerine dönüştürür ve bu vektörleri bir RNN'e besler.
- **Decoder (Kod Çözücü):** Kodlayıcıdan gelen vektörleri alır ve çıkış dizisini oluşturur. Genellikle bir başlangıç belirteci (#START#) ile başlayarak, bir sonraki kelimeyi tahmin etmek için bir RNN'e beslenir. Bu tahmin, bir sonraki kelimenin olasılık dağılımını bir yoğun katmana gönderir. En yüksek olasılığa sahip kelime çıkış olarak kabul edilir ve kod çözücüye geri beslenir. Bu işlem, bir sonraki kelimeyi tahmin etmek için tekrarlanır ve çıkış dizisi tamamlanana kadar devam eder.

**Çalışma Adımları**
1. Her giriş metni ve çıkış metni, belirli bir maksimum uzunluğa (maxlen) kırpılır veya doldurulur. Metinler, belirli bir kelime dağarcığı ile sınırlandırılır ve kelimeler belirli bir sayıda benzersiz tokenlere dönüştürülür.
2. Kodlayıcı, giriş metnini temsil eden "context (bağlam" adı verilen bir vektör üretir. Bu vektör, giriş metninin anlamını sıkıştırılmış bir biçimde kodlar.
3. Kod çözücü, kodlayıcıdan gelen vektörü alır ve çıkış metnini oluşturur.
4. Kodlayıcı ve kod çözücü ağları birleştirilir ve bir Seq2Seq modeli oluşturulur. Model, eğitim verisi üzerinde eğitilir. Bu, giriş metinlerinin kodlayıcının girişine beslenmesi ve çıkış metinlerinin kod çözücünün çıkışından tahmin edilmesiyle yapılır. Modelin çıkışları, gerçek çıkış metinlerine göre değerlendirilir ve bir kayıp fonksiyonu kullanılarak gerçek ve tahmin edilen çıkış arasındaki fark hesaplanır. Model, geriye doğru yayılım algoritması (backpropagation) kullanılarak bu kayıp fonksiyonunu minimize etmek için güncellenir.

**Attention (Dikkat) Tekniği**
Seq2seq modelinde, kodlayıcı çıktısının uzun cümleleri zorlaştırdığı ve darboğaz yaptığı ortaya çıktı. Bunun için 2014 yılında Bahdanau ve diğerleri tarafından, 2015 yılında Luong ve diğerleri tarafından "Attention (Dikkat)" tekniği önerildi. Attention mekanizması, kod çözücü ağının her adımında, her bir giriş kelimesine odaklanmasına izin vererek çalışır. Yani kod çözücü ağı çıkışın her bir kelimesini oluştururken, giriş dizisindeki her bir kelimenin önemini değerlendirir ve çıkışın o kelimeyi üretirken girişin hangi kısımlarına odaklanması gerektiğin karar verir.

1. Kodlayıcı, giriş dizisini temsil eden bir vektörler dizisi üretir. 
2. Her kod çözücü adımında, kod çözücü, bir hedef kelime üretmek için giriş dizisinin hangi kısımlarına odaklanması gerektiğini belirlemek için "attention skorları" hesaplar. Attention skorları, kod çözücünün mevcut gizli durumu ve kodlayıcı çıktıları arasındaki benzerlikleri ölçer.
3. Attention skorları, kodlayıcı çıktılarına ağırlık vermek için kullanılır. Yani, kod çözücü, önemli bulduğu giriş kelimesine daha fazla dikkat gösterir. Bu ağırlıklı kodlayıcı çıktıları, kod çözücünün mevcut durumuna (hidden state) eklenir.
4. Ağırlıklı kodlayıcı çıktıları, kod çözücü ağında bir sonraki gizli durumu hesaplamak için kullanılır. Bu gizli durum, bir sonraki çıkış kelimesini tahmin etmek için yoğun bir katmana (dense layer) beslenir.

Bu şekilde, attention mekanizması, kod çözücünün her adımında giriş dizisinin farklı kısımlarına odaklanmasını sağlar. Bu da Seq2Seq modelinin uzun cümleler gibi zorlu durumlarda daha iyi performans göstermesini sağlar.

