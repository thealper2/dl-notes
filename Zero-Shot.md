Zero-shot classification, geleneksel sınıflandırma yöntemlerinden farklı olarak, eğitim aşamasında önceden belirlenmiş bir sınıf kümesi olmadan veri türlerini otomatik olarak tanımlamak için kullanılır. Bu, modelin, eğitim verilerindeki sınıfların herhangi biriyle etkileşime girmeden yeni ve görülmemiş sınıfları tanımlama yeteneğine dayanır. Zero-shot classification, belirli bir veri noktasını veya örneği belirli bir sınıfa atamak için bir özelik vektörü kullanır. Bu özellik vektörü, ilgili verinin temsilini sağlar ve bu temsil, modelin belirli sınıflar arasında benzerlikleri ve farklılıkları belirlemesine olanak tanır.
- **Görülen (Seen) Sınıflar:** Eğitim aşamasındaki verilerin etiketleridir.
- **Görülmeyen (Unseen) Sınıflar:** Eğitim aşamasında verilerde bulunmayan etiketlerdir.

**Öğrenme Türleri**
- **Inductive Zero-Shot:** Sınıflandırma modelinin eğitim aşamasında kullanılan sınıf etiketleri ile ilgili sınıf bilgileri dışında yeni sınıfları tahmin ederken kullanılan özelliklerdir. Model, eğitim aşamasında belirli bir sınıf kümesi ile önceden eğitilir ancak bu sınıflar dışında sınıflar için belirli bir bilgiye sahip değildir.
- **Transductive Zero-Shot:** Modelin eğitim aşamasındaki sınıf etiketlerine ile ilgili sınıf bilgilerinin yanına yeni ve görüşmemiş sınıfların özelliklerini içeren ek bilgileri kullanır. Daha sonra tahmin yaparken yeni sınıfların özelliklerine dayanarak bu ek bilgileri kullanarak tahminlerde bulunabilir.

**Öğrenme Metodları**
- **Gömme Tabanlı Yöntemler:** Önceden belirlenmiş sınıflar arasındaki ilişkileri temsil etmek için sınıfların özellik gömümlerini kullanır. Her sınıf, bir vektör uzayında benzersiz bir konumu temsil eden bir gömme vektörüne sahiptir. Bu gömme vektörleri, sınıfların özelliklerini ve aralarındaki ilişkileri yansıtır. Yeni bir sınıf belirlendiğinde, bu sınıfın özellik gömümleri, mevcut sınıf gömme vektörleri arasında yer alacak şekilde tahmin edilir. Gömme tabanlı yöntemlerin dezavantajı bias ve alan kayması sorunudur. Model, daha önceden eğitilmiş sınıfların etiketleri tahmin etmeye yönelik bir yanlılık gösterir. Model, tahmin edilecek verinin özellik gömümlerini doğru olarak eşleyebilmeyi garanti etmez.
- **Üretken Model Tabanlı Yöntemler:** Önceden eğitilmiş bir model kullanır. Yeni bir sınıf belirlendiğinde, bu sınıfın özelliklerini tahmin etmek için önceden eğitilmiş modelin yetenekleri kullanır. Önceden eğitilmiş model, yeni sınıfları tanımlamak için kullanılmadan önce, sınıflar arasındaki ilişkileri öğrenmek için önceden eğitilmiş bir veri seti üzerinde fine-tuning işleminden geçirilir.

```python
from transformers import pipeline

classifier = pipeline("zero-shot-classification")

# Örnek metin ve sınıflar
text = "Birçok renkli balon gökyüzüne uçtu."
candidate_labels = ["spor", "sanat", "bilim", "yemek"]

# Sınıflandırma
result = classifier(text, candidate_labels)

# Sonuçları yazdırma
print("Metin:", text)
print("Tahmin edilen sınıf:", result['labels'][0])
print("Sınıfın olasılığı:", result['scores'][0])
```

