Latent Semantic Analysis (LSA), metin belgelerindeki gizli semantik ilişkileri keşfetmek ve belgeler arasındaki benzerlikleri ölçmek için kullanılır. Temelde, belge koleksiyonundaki terimler arasındaki ilişkileri keşfetmek için bir dizi matematiksel dönüşüm ve indirgeme işlemi yapar.

**Çalışma Adımları**
1. **Belge Koleksiyonu Hazırlama**: Analiz için bir metin belgesi koleksiyonu hazırlanır. Bu belgeler önceden işlenmiş ve gerektiğinde metin temizleme işlemlerinden geçirilmiş olmalıdır.
2. **Terim-Frekans Matrisinin Oluşturulması**: Belge koleksiyonundaki her terimin ve her belgenin terim frekanslarına dayalı bir matris oluşturulur. Bu matris, belge koleksiyonunun boyutlarına ve terimlerin sıklığına bağlı olarak büyük olabilir.
3. **TF-IDF Ağırlıklarının Hesaplanması**: Terim-frekans matrisindeki sıklık bilgileri, TF-IDF ağırlıkları kullanılarak dönüştürülebilir. Bu, terimlerin belgeler içindeki önemini vurgulamak için kullanılır.
4. **SVD (Singular Value Decomposition) Uygulanması**: TF-IDF matrisi, SVD gibi bir matris ayrıştırma tekniği uygulanarak düşük boyutlu bir matrise dönüştürülür. Bu, matrisin boyutunu azaltarak ve gizli semantik ilişkileri vurgulayarak yapılır.
5. **Konsept Vektörlerinin Oluşturulması**: SVD'den elde edilen düşük boyutlu matris, her bir belge için bir konsept vektörü olarak kullanılır. Bu vektörler, belgeler arasındaki semantik benzerlikleri temsil eder.
6. **Benzerlik Ölçüsünün Hesaplanması**: Belirli bir benzerlik metriği (örneğin, kosinüs benzerliği) kullanılarak, belgeler arasındaki benzerlik ölçülür. Bu, belge koleksiyonundaki belgelerin karşılıklı olarak nasıl ilişkili olduğunu anlamak için kullanılır.

```python
from gensim import corpora
from gensim.models import LsiModel
from gensim.matutils import corpus2dense
from pprint import pprint

# Örnek metin belgeleri
documents = [
    "Gemini modeli ortaya çıktı.",
    "Yapay zeka modeli SORA tanıtıldı.",
    "Makine öğrenimi güzeldir.",
    "Bu problem için makine öğrenimi kullanılabilir."
]

# Belge koleksiyonunu bir kelime listesi olarak tokenize edin
text_data = [[word for word in document.lower().split()] for document in documents]

# Bir kelime-sayma modeli oluşturun
dictionary = corpora.Dictionary(text_data)

# Belge terim matrisini oluşturun (BoW modeli)
corpus = [dictionary.doc2bow(text) for text in text_data]

# LSA modelini eğitin
lsi_model = LsiModel(corpus=corpus, id2word=dictionary, num_topics=2)

# LSA modelini kullanarak belgeleri dönüştürün
lsi_corpus = lsi_model[corpus]

# LSA modelinin özdeğerlerini ve özvektörlerini alın
lsi_matrix = corpus2dense(lsi_corpus, num_terms=2)

# Sonuçları yazdırın
pprint(lsi_model.print_topics())
print("LSA Matrix:")
print(lsi_matrix)
```

