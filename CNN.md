CNN (Evrişimsel sinir ağı veya ConvNet), görüntü tanıma problemlerinde kullanılır. Bir girdi görüntüsü alarak, görüntüdeki çeşitli nesnelere önem atayan (ağırlık ve bias) bir derin öğrenme algoritmasıdır.
- Convolutional Layer - Özellik çıkarmak için kullanılır. Bu katmanda filtreler yer alır. Çekirdekteki değerler görüntü üzerinde kaydırılır ve değerler görüntünün değerleriyle çarpılır. Elde edilen değerler toplanır. Örneğin, 6x6'lik bir görüntüye 2x2 lik bir filter uygulandığında yeni görüntü 4x4 lük olur. Bu işlem tüm görsele uygulanır.
- Activation Layer - Her konvolüsyon katmanından sonra aktivasyon işlemi uygulanır. Genellikle ReLU gibi doğrusal olmayan aktivasyon işlevleri kullanılır. Bu, ağın daha karmaşık ve genel özellikler öğrenmesine yardımcı olur.
- Pooling Layer - Özellik haritalarının boyutunu küçültmek ve ağı daha da hızlandırmak için kullanılır. 
- Flattening Layer - Veriyi 1x1 haline getirir. Böylece veri FC katmanının girişine hazırlanmış olur.
- Fully-Connected Layer: Çıktılar sınıflandırılmak üzere bu katmandan geçirilir. Bu katmanlar, özellik haritalarını düzleştirir ve "softmax" gibi bir aktivasyon işlemi ile sınıflandırma sonuçlarını üretir.

# R-CNN
Region-Based CNN, görüntü nesnelerinin algılanması ve sınıflandırılması için kullanılan bir tekniktir. R-CNN, Convolutional Neural Networks (CNN) ve nesne algılama tekniklerini bir araya getirerek nesneleri tanımak ve çerçevelemek için kullanılır.

R-CNN, aşağıdaki temel adımları içerir:
1. **Bölge Önerileri (Region Proposals):** İlk adımda, görüntü üzerinde potansiyel nesne bölgelerini belirlemek için seçici arama (Selective Search) gibi bir yöntem kullanılır. Bu adım, görüntüyü bölgelere böler ve her bir bölgenin içerisinde muhtemel bir nesne bulunduğu düşünülen bölgeleri seçer.
2. **Özellik Çıkarma (Feature Extraction):** Her bölge, bir CNN kullanılarak özellik vektörlerine dönüştürülür. Bu özellik vektörleri, belirli nesne bölgelerini temsil eden özellikleri içerir.
3. **Sınıflandırma:** Özellik vektörleri, bir sınıflandırma algoritması ile sınıflandırılır. Bu adım, her bölgenin hangi sınıfa ait olduğunu belirler.
4. **Birleştirme (Bounding Box Regression):** Bölge önerileri, nesnelerin sınırlayıcı kutularını belirlemek için bir regresyon modeli kullanılarak düzeltilir. Bu, nesne sınırlayıcı kutularının daha iyi hizalanmasına yardımcı olur.

R-CNN, nesne algılamada oldukça etkili olsa da, işlemci ve bellek açısından oldukça maliyetlidir, çünkü her bölge önerisi ayrı ayrı işlenir. Bu nedenle daha sonraki çalışmalar, R-CNN'nin hızını artırmak ve daha efektif hale getirmek için farklı türevler geliştirdi.

# Fast R-CNN
Fast R-CNN (Fast Region-based Convolutional Neural Network), nesne algılama alanında etkili bir yöntemdir ve özellikle Convolutional Neural Networks (CNN) tabanlı nesne algılama modellerini hızlandırmak için tasarlanmıştır. Fast R-CNN, girdi görüntüsündeki nesneleri algılamak ve çerçevelemek için bir bölge tabanlı yaklaşım kullanır, ancak önceki versiyonlara göre daha hızlıdır.

Fast R-CNN, aşağıdaki temel bileşenlerden oluşur:
1. **Bölge Önerileri (Region Proposals):** Fast R-CNN, görüntüdeki olası nesne bölgelerini belirlemek için önceden eğitilmiş bir seçici arama (Selective Search) veya benzeri bir yöntem kullanır. Bu adım, muhtemel nesne bölgelerini tanımlar ve sınıflandırır.
2. **Özellik Haritası Oluşturma (Feature Map Generation):** Görüntü, bir evrişim ağı (CNN) kullanılarak özellik haritasına dönüştürülür. Bu, her bölge önerisi için özellik vektörlerini elde etmek için kullanılır.
3. **Özellik Vektörlerini Düzleştirme (Flatten Feature Vectors):** Özellik haritaları, her bir bölge önerisi için tek bir özellik vektörüne dönüştürülür.
4. **Sınıflandırma ve Sınırlayıcı Kutu Regresyonu (Classification and Bounding Box Regression):** Özellik vektörleri, bir sınıflandırma ağı ve bir sınırlayıcı kutu regresyon ağı kullanılarak aynı anda sınıflandırılır ve sınırlayıcı kutuları (bounding box) belirlenir. Bu, her bölge önerisinin hangi sınıfa ait olduğunu ve nesnenin sınırlayıcı kutusunun nasıl olması gerektiğini belirler.

Fast R-CNN, özellikle önceki R-CNN versiyonlarına (Region-CNN) göre daha hızlıdır, çünkü tüm işlemleri tek bir CNN modelinde gerçekleştirir.

# Mask R-CNN
Mask R-CNN (Mask Region-based Convolutional Neural Network), nesne algılama ve nesne segmentasyonu (maskelenmiş nesne bölgelerini belirleme) görevlerini gerçekleştirmek için kullanılan gelişmiş bir derin öğrenme modelidir. Mask R-CNN, özellikle nesne algılamanın yanı sıra nesne bölgelerinin kesin piksel düzeyinde tanımlanması gereken görevlerde etkilidir.

Mask R-CNN, aşağıdaki temel özelliklere sahiptir:
1. **Bölge Önerileri (Region Proposals):** Mask R-CNN, görüntüdeki potansiyel nesne bölgelerini belirlemek için bir bölge önerisi ağı (Region Proposal Network, RPN) kullanır. RPN, olası nesne bölgelerini önerir ve bu bölgeler daha sonra detaylı işlem için kullanılır.
2. **Özellik Çıkarma (Feature Extraction):** Görüntü, bir evrişim ağı (CNN) kullanılarak özellik haritasına dönüştürülür. Bu özellik haritası, her bölge için ayrı ayrı özellik vektörleri üretmek için kullanılır.
3. **Sınıflandırma:** Mask R-CNN, her bölge için nesne türünü (sınıfı) belirlemek için bir sınıflandırma ağı kullanır. Bu, nesnelerin ne olduğunu sınıflandırır.
4. **Sınırlayıcı Kutu Regresyonu (Bounding Box Regression):** Nesne sınırlayıcı kutuları, bölge önerilerini düzeltmek ve daha iyi hizalamak için bir regresyon modeli kullanılarak hesaplanır.
5. **Maske Tahmini:** Mask R-CNN, her bölge için maske tahmini yapmak için bir maske ağı kullanır. Bu, nesnenin her pikselinin nesneye ait olma olasılığını tahmin eder, böylece nesne bölgeleri kesin olarak belirlenir.

Mask R-CNN, özellikle medikal görüntüleme, otonom sürüş, nesne izleme ve insan tanıma gibi birçok uygulama alanında kullanılır. Mask R-CNN, nesneleri algılamanın yanı sıra, bu nesnelerin piksel düzeyinde kesin segmentasyonunu sağladığı için oldukça hassas ve ayrıntılı sonuçlar üretebilir.

