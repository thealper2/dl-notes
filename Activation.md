### Aktivasyon Fonksiyonları Çeşitleri

1. Step Function - Basamak Fonksiyonu
2. Linear Function - Doğrusal Fonksiyon
3. Sigmoid Function
4. Tanh Function - Hiperbolik Tanjant Fonksiyonu
5. ReLU (Rectified Linear Unit) Function
6. Leaky ReLU Function - Sızıntılı ReLU Fonskiyonu
7. Parameterized ReLU Function
8. Exponential ReLU Function
9. Softmax Function
10. Swish (A Self-Gated) Function - Kendinden Geçitli Fonksiyon

# Step Function
Step fonksiyonu, basit ve kesikli bir aktivasyon fonksiyonudur. Belirli bir eşiği aşan girişlere 1, aşmayanlara ise 0 değerini verir. İkili sınıflandırma (binary classification) problemleri üzerinde kullanılır. Özellikle basit ve lineer ayrılabilir veri kümeleri için kullanılır. Genellikle çıkış katmanlarında (output layer) kullanılır. Türevi 0 olduğu için geri yayılım sırasında parametreler güncellenmez yani öğrenme süreci gerçekleşmez. Bundan dolayı gizli katmanlarda (hidden layer) tercih edilmez.

```scss
f(x) = {
	1, x > 0
	0, x =< 0
}
```

**Avantajlar**
- Basit ve yüksek kesinlikle belirli sınıf sınırları oluşturur.
- Kesikli doğası sayesinde yüksek hızda hesaplamalar yapabilir.

**Dezavantajlar**
- Kesikli doğası nedeniyle, gradyan tabanlı eğitim algoritmaları (geri yayılım vb.) ile kullanılması zordur.
- Sıfır gradyanı nedeniyle, step fonksiyonunun türevi sıfırdır ve eğitim süreci sorunlu hale gelir. Bu, öğrenme sürecinin durmasına yol açar.
- Doğrusal olmayan ilişkileri modellemekte yetersiz kalır.
- Çoklu sınıflandırma problemlerinde kullanılamaz çünkü sadece iki çıkış sınıfı (0 ve 1) üretir.

---
# Linear Function
Linear fonksiyon, girişin herhangi bir dönüşüm olmadan çıkışa aktarıldığı bir doğrusal ilişki oluşturur. Girişi doğrudan çıkış olarak iletir. Türevi sabit bir değere eşit olduğu için öğrenme süreci gerçekleşmez. Genellikle regresyon problemlerinde kullanılır. 

```scss
f(x) = x
```

**Avantajlar**
- Basittir.
- Doğrusal problemler için uygundur. Giriş ve çıkış arasındaki doğrusal ilişkileri ifade eder.

**Dezavantajlar**
- Sadece doğrusal ilişkileri modelleyebilirler.
- Sınırlı işlemsel yeteneğe (sadece girişi iletmek) sahip oldukları için karmaşık problemlerde yetersiz kalırlar.

---
# Sigmoid Function
Sigmoid (Logistic) fonksiyonu, giriş verisini 0 ile 1 arasında bir çıkışa döndüren bir S-şeklinde eğri oluşturur. Giriş verilerini bir olasılık dağılımına dönüştürmek için yaygın olarak kullanılır. İkili sınıflandırma problemlerinde kullanılır. Doğrusal olmayan (non-linear) bir fonksiyondur. Karar vermeye yönelik olasılıksal bir yaklaşımdır. 

```scss
f(x) = 1 / (1 + e^(-x))
```

**Avantajları**
- Sürekli ve türevlenebilirdir. Böylece gradyan tabanlı öğrenme algoritmalarıyla kullanılması kolaylaşır.

**Dezavantajları**
- Sigmoid fonksiyonunun eğrisi, girişler büyük veya küçük olduğunda gradyanların kaybolmasına neden olabilir. Bu, derin sinir ağlarında eğitim sırasında sorunlara yol açabilir ve "gradyan kaybı (vanishing gradient)" problemine neden olabilir.
- Sıfır merkezli değildir. Sigmoid fonksiyonunun orta noktası 0 değil, 0.5'tir. Bu, girişlerin çok büyük veya çok küçük olduğunda gradyanın hızla azalmasına yol açabilir.
- Sigmoid fonksiyonu, özellikle çok büyük ağırlıklar veya girişlerle, yavaş yakınsayan bir eğime sahiptir. Bu, öğrenme sürecini yavaşlatabilir.

---
# Tanh Function
Tanh fonksiyonu, giriş verilerini -1 ile 1 arasında bir çıkışa döndüren bir S-şeklinde eğri oluşturur. İkili sınıflandırma ve çoklu sınıf sınıflandırma problemlerinde kullanılabilir. Daha büyük ve karmaşık veri kümeleri için sigmoid fonksiyonuna göre daha güçlüdür. 

```scss
f(x) = (e^x - e^(-x)) / (e^x + e^(-x))

f(x) = 2sigmoid(2x)-1
```

**Avantajları
- Sıfır merkezlidir. Bu, girişler çok büyük veya çok küçük olduğunda gradyan kaybı (vanishing gradient) sorununu azaltır.
- Sürekli ve türevlenebilirdir.

**Dezavantajları**
- Gradyan kaybolması (gradyan vanishing) sorununa sahip.
- 0 merkezli olmasından dolayı ağırlıkların ve çıkışların değişken işaretlerde olmasına neden olabilir. Bu da eğitim sürecini karmaşıklaştırabilir.

---
# ReLU Function
ReLU fonksiyonu, girişin pozitif olduğu durumlarda doğrusal bir çıkış üretir ve negatif olduğu durumlarda sıfır çıkış verir. Genellikle binary classification, multiclass classification, regresyon ve diğer çeşitli problemlerde etkili sonuçlar verir. ReLU fonksiyonunun avantajı aynı anda tüm nöronları aktive etmemesidir.

```scss
	                x if x >= 0  
g(x) = max(0, x) =  
	                0 if x < 0
```

**Avantajları**
- Basittir.
- Pozitif girişleri olduğu gibi bıraktığı için hesaplamaları hızlandırır.
- ReLU'nun türevi her yerde tanımlıdır (giriş negatifken 0, pozitifken 1), bu da gradyan kaybı sorununu azaltır ve derin sinir ağlarının daha iyi eğitilmesini sağlar.
- Doğrusal olmayanlığı ekler ve ağın karmaşıklığını artırır.

**Dezavantajları**
- Giriş negatif olduğunda sıfır çıkış verir, bu da bazı nöronların eğitim sırasında "ölmesine" yol açabilir. Yani, bu nöronlar artık güncellenmez ve hiçbir katkıda bulunmaz.
- Bazı problemlerde doğrusal olmayanlık sınırlarını zorlayamaz ve bu nedenle tüm problemler için uygun değildir.

---
# Parameterized ReLU Function
PReLU, giriş verilerini işlerken, negatif değerler için bir hiperparametre kullanır, bu da fonksiyonun giriş verisine bağlı olarak negatif değerler için farklı eğriler oluşturmasına izin verir. PReLU, özellikle derin öğrenme modellerinde "ölme" sorununu hafifletmeye yardımcı olur. 

```scss
f(x) = x, x > 0 
f(x) = alpha * x, x <= 0
```

**Avantajları**
- PReLU, negatif girişler için eğim belirleyen alpha hiperparametresi kullanarak "ölme" sorununu hafifletir. Bu, negatif girişler için gradyanların sıfır olmasını engeller ve modelin daha iyi eğitilmesini sağlar.
- PReLU, giriş pozitif olduğunda doğrusal bir davranış sergilerken, giriş negatif olduğunda doğrusal olmayan davranış sergiler. Bu, daha karmaşık veri yapılarını ve ilişkilerini modellemek için kullanışlıdır.
- PReLU'nun eğimi öğrenilebilir bir parametre olduğu için, modelin eğimini veriye uyum sağlaması ve daha iyi sonuçlar elde etmesi sağlanır.

**Dezavantajları**
- PReLU'nun eğimi öğrenilebilir olduğu için, hesaplama maliyeti biraz daha yüksektir.
- Alpha hiperparametresi belirlenmelidir ve bu, modelin performansını etkileyebilir. Alpha'nın uygun bir değerini bulmak, deneme yanılma gerektirebilir.

---
# Exponential ReLU Function
Giriş verilerini işlerken negatif değerler için bir hiperparametre kullanır ve giriş verisine bağlı olarak negatif değerler için farklı bir eğri oluşturur. EReLU, ReLU'nun bazı dezavantajlarını hafifletmek amacıyla tasarlanmıştır. 

```scss
f(x) = x, x > 0
f(x) = alpha * (e^x - 1), x <= 0
```

**Avantajları**
- EReLU, negatif girişler için eğim belirleyen alpha hiperparametresi kullanarak "ölme" sorununu hafifletir. Bu, negatif girişler için gradyanların sıfır olmasını engeller ve modelin daha iyi eğitilmesini sağlar.
- EReLU, giriş pozitif olduğunda doğrusal bir davranış sergilerken, giriş negatif olduğunda doğrusal olmayan davranış sergiler. Bu, daha karmaşık veri yapılarını ve ilişkilerini modellemek için kullanışlıdır.
- EReLU'nun eğimi öğrenilebilir bir parametre olduğu için, modelin eğimini veriye uyum sağlaması ve daha iyi sonuçlar elde etmesi sağlanır.

**Dezavantajları**
- EReLU'nun eğimi öğrenilebilir olduğu için, hesaplama maliyeti biraz daha yüksektir.
- Alpha hiperparametresi belirlenmelidir ve bu, modelin performansını etkileyebilir. Alpha'nın uygun bir değerini bulmak, deneme yanılmaya ihtiyaç duyabilir.

---
# Leaky ReLU Function
Leaky ReLU fonksiyonu, girişin pozitif olduğu durumlarda doğrusal bir çıkış üretirken, giriş negatif olduğunda sıfır yerine küçük bir negatif değer döndürür. Bu, ReLU'nun (Rectified Linear Unit) "ölme" sorununu hafifletmeyi amaçlar. Leaky ReLU'nun performansı, alpha hiperparametresinin iyi bir şekilde ayarlanmasına bağlıdır.

```scss
f(x) = x, x > 0 
f(x) = alpha * x, x <= 0
```

**Avantajları**
- Negatif girişler için küçük bir negatif gradyan eklediği için, "ölme" sorununu hafifletir ve ağın daha iyi eğitilmesini sağlar.
- Türevlenebilir olduğu için gradyan tabanlı öğrenme algoritmalarıyla kullanılabilir.
- Girişlerin çok büyük veya çok küçük olduğunda gradyan sorunlarına karşı daha dirençlidir.

**Dezavantajları**
- Leaky ReLU'da alpha hiperparametresi seçilmelidir, ve bu değer seçimine hassas olabilir.
- Leaky ReLU, ReLU'ya göre daha yavaş yakınsayabilir.

---
# Softmax Function
Softmax fonksiyonu, çoklu sınıf sınıflandırma problemlerinde kullanılan bir aktivasyon fonksiyonudur. Giriş verilerini sınıflar arasında olasılık dağılımına dönüştürür. Softmax fonksiyonu, her sınıfın olasılığını tahmin etmek için kullanılır. 

```scss
f(x)_i = e^(x_i) / ∑(e^(x_j)) for j = 1 to N
```

**Avantajları**
- Sınıflar arasında olasılık dağılımı üretir, bu nedenle çoklu sınıf sınıflandırma problemleri için uygundur.
- Giriş verilerini normalize eder, yani her bir sınıfın olasılığını 0 ile 1 arasında bir değere dönüştürür ve tüm sınıfların toplamı 1 olur.
- Gradyan tabanlı eğitim algoritmalarıyla uyumlu ve türevlenebilirdir.

**Dezavantajları**
- İkili sınıflandırma problemleri için çok fazla karmaşıklık ekler ve diğer aktivasyon fonksiyonları daha uygun olabilir.
- Modelin görmediği sınıf etiketlerini kabul etmeye meyilli olabilir ve bu, modelin yanıltıcı sonuçlar üretmesine yol açabilir.

---
# Swish Function
Swish fonksiyonu, giriş verilerini bir doğrusal fonksiyon ve sigmoid fonksiyonun birleşimi ile işler. Swish fonksiyonu, özellikle derin öğrenme modellerinde ve özyinelemeli sinir ağları (RNN) gibi bazı uygulamalarda kullanılır.

```scss
f(x) = x * sigmoid(x)
```

**Avantajları**
- Swish fonksiyonu, giriş pozitif olduğunda doğrusal bir davranış sergilerken, giriş negatif olduğunda doğrusal olmayan davranış sergiler. Bu, daha karmaşık veri yapılarını ve ilişkilerini modellemek için kullanışlıdır.
- Swish, ReLU gibi kesikli türevlere sahip değildir, bu nedenle gradyan tabanlı eğitimde daha pürüzsüz bir davranış sergiler.

**Dezavantajları**
- Hesaplama maliyeti yüksektir.
- Swish fonksiyonunda bir hiperparametre olmadığı için, hiperparametre ayarıyla ilgili daha az esnekliğe sahiptir.

