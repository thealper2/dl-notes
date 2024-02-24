1. SGD
2. RMSprop
3. Adam
4. AdamW
5. Adadelta
6. Adagrad
7. Adamax
8. Adafactor
9. Nadam
10. Ftrl
11. Lion

---
#  SGD (Stochastic Gradient Descent)

Gradyan azalmada tüm veri seti kullanılırken stokastik gradyan azalmada tek bir örneklem kullanılır. Her bir adımda bir örnek seçer ve bu örneğe göre gradyanı hesaplar. Bu yüzden "stokastik" olarak adlandırılır. Küçük veri kümelerinde kullanışlıdır. Tek örnek ile işlem yapıldığı için global minimuma doğru kararlı bir şekilde ilerleme görülmez. Minimaya ulaşmak için daha fazla iterasyon sayısına ihtiyaç duyar.

# RMSprop (Root Mean Square Propagation)
Gradyanlara bağlı olarak öğrenme oranını (learning rate) ayarlar. Her parametreyi ayrı ayrı günceller. Eğer bir boyutta gradyanlar büyük ise RMSprop tarafından hesaplanan güncelleme oranı düşer; küçük ise güncelleme oranı artar. Daha az varyans gösteren parametreler daha fazla güncellenir; daha fazla varyans gösteren parametreler daha az güncellenir. Büyük veri setlerinde iyi çalışır.

# Adam (Adaptive Moment Estimation)
Momentum ve RMSprop yöntemlerinin birleşimidir. Birinci ve ikinci momentlerin (hareketli ortalama) eksponensiyel bir şekilde azalan ortalama değerlerini korur ve bu sayede gradyanları güvenilir bir şekilde tahmin eder. Gürültülü veri setleri için uygundur. 

# AdamW
Adam yöntemine ağırlık çarpımı (weight decay) eklenmiş bir versiyonudur. Ağırlık çarpımı, modelin karmaşıklığını kontrol etmek ve aşırı uydurmaya karşı koymak için kullanılan bir tekniktir.

# Adadelta
Parametrelerin güncellenmesi için her adımda değişen bir öğrenme oranı kullanır. Bu oran, parametrelerin hareketli ortalaması ile gradyanın hareketli ortalamasının oranına bağlı olarak hesaplanır. Böylece, büyük gradyanlara küçük, küçük gradyanlarda büyük güncellemeler yapılır.

# Adagrad
Her parametreyi ayrı ayrı güncellerken, daha önceki gradyanların karelerinin toplamını kullanarak öğrenme oranını adapte eder. Daha sık rastlanan gradyan bileşenlerine daha küçük, daha nadir rastlanan gradyan bileşenlerine daha büyük bir öğrenme oranı verilmesini sağlar. Böylece öğrenme oranının manuel olarak ayarlama ihtiyacını kaldırır. Eğitim ilerledikçe, gradyanların karelerinin kümülatif toplamı büyüdükçe, öğrenme oranı küçülür. Bu da eğitim ilerledikçe öğrenme oranının çok hızlı bir şekilde azalmasına neden olabilir.