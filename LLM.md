Büyük miktarda metin verisiyle eğitilir. Bir dilin yapısal ve istatistiksel özelliklerini öğrenir ve dilin bir sonraki kelimesini veya dizisini tahmin etmek için kullanılır.

**Pretraining (Ön Eğitim):** Pretraining aşamasında, dil modeli büyük miktarda genel dil verisiyle eğitilir. Bu genel dil verisi, dil modelinin dilin genel yapısal ve istatistiksel özelliklerini öğrenmesine olanak tanır. Bu aşama, modelin dil örüntülerini ve ilişkilerini genel olarak öğrenmesini sağlar ve daha spesifik görevler için özelleştirilmiş eğitim verisiyle fine-tuning aşamasına geçilir.

**Fine-tuning (İnce Ayar):** Fine-tuning aşamasında, pretraining aşamasında eğitilmiş olan dil modeli, daha spesifik bir görev veya veri kümesi üzerinde daha fazla eğitilir. Örneğin, metin sınıflandırma, dil çevirisi veya metin üretimi gibi belirli bir NLP görevi için dil modeli, bu görev için özelleştirilmiş eğitim verisiyle fine-tuning yapılır. Bu aşamada, model daha spesifik dil örüntülerini ve ilişkilerini öğrenir ve belirli bir görevde daha iyi performans göstermesini sağlar.

# Fine-tuning Yöntemleri
1. **Tam Katmanlarını Eğitmek:** Bu yöntemde, dil modelinin tüm katmanları belirli bir görev için özelleştirilmiş eğitim verisiyle birlikte yeniden eğitilir. Bu, dil modelinin tamamen görev spesifik hale gelmesini sağlar.
2. **Özel Katmanları Eğitmek:** Bu yöntemde, dil modelinin belirli bir görev için özelleştirilmiş eğitim verisiyle birlikte sadece bazı katmanları yeniden eğitilir. Bu yaklaşım, daha az eğitim verisi gerektirebilir ve genellikle daha hızlı bir fine-tuning süreci sunar.
3. **Transfer Learning (Aktarım Öğrenimi):** Bu yöntemde, dil modeli, pretraining aşamasında genel dil özelliklerini öğrendikten sonra, özelleştirilmiş bir görev için sınırlı miktarda eğitim verisiyle yeniden eğitilir. Transfer learning, genellikle benzer veya ilişkili bir görevden öğrenilen bilgilerin daha spesifik bir görevde kullanılmasını sağlar.
4. **Kademeli Unfreeze (Aşamalı Çözülme):** Bu yöntemde, dil modelinin katmanları aşamalı olarak özelleştirilmiş eğitim verisiyle birlikte yeniden eğitilir. Daha sonra, daha düşük seviyeli katmanlar da sırayla açılır ve eğitilir. Bu yaklaşım, önceki katmanların öğrendiği genel dil özelliklerini korurken, daha spesifik bir görev için modelin daha alt seviyeli özellikleri öğrenmesini sağlar.

# Fine-tuning Metodları
1. **PEFT (Prompt-based Fine-tuning):** Özel bir komut dizisi (prompt) kullanarak dil modelini belirli bir görev için özelleştiren bir fine-tuning yöntemi.
2. **IGBI (Iterative Gradient-based Instance Reweighting):** Eğitim verisindeki örneklerin ağırlıklarını iteratif olarak ayarlayarak dil modelini belirli bir görev için özelleştiren bir fine-tuning yöntemi.
3. **KD (Knowledge Distillation):** Büyük ve karmaşık bir dil modelinden (örneğin, bir öğretmen model) daha küçük bir dil modeline (örneğin, bir öğrenci model) bilgi aktararak fine-tuning yöntemi.
4. **PT (Prompt Tuning):** Dil modelini belirli bir görev için özelleştirmek için tasarlanmış özel bir komut dizisi (prompt) kullanarak fine-tuning yöntemi.
5. **ALUM (Adaptive Large Batch Update Momentum):** Büyük toplu güncellemeleri (large batch updates) kullanarak dil modelini özelleştiren bir fine-tuning yöntemi.
6. **GATE (Guided Attention Training):** Attention mekanizmasını yönlendirmek için bir rehber kullanarak dil modelini özelleştiren bir fine-tuning yöntemi.

# LLM Riskleri
1. Bias: Eğitim seti belirli fikirlere yatkınlık içeriyorsa model de bu şekilde önyargılı sonuçlar üretebilir.
2. Karbon Emisyonu: Modellerin eğitiminde kullanılan GPU'lar çok miktarda enerji tüketir.
3. Halüsinasyonlar: Model gerçekdışı ve yanlış bilgiler üretebilir.
4. Güvenlik: Model kötü amaçlara yardımcı olabilir.
5. Rıza: Kullanıcıların modele gönderdiği bilgiler açık izinlidir. Yani model bu bilgileri kullanabilir.

