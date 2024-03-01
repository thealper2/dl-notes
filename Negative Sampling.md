Word embedding modelleri gibi yoğun doğrusal olmayan modellerin eğitimi sırasında sıklıkla kullanılan bir öğrenme stratejisidir. Bu strateji, eğitim veri setindeki her örneği tamamen incelemek yerine, yalnızca küçük bir alt kümesini seçerek hesaplama maliyetini azaltır. Negative sampling, özellikle yüksek boyutlu veri setleri üzerinde eğitilen word embedding (kelime gömme) modelleri için önemlidir. Word2vec gibi modellerde kullanılır. Bu tür modeller, milyonlarca kelime vektörünü öğrenmek için büyük veri setlerine ihtiyaç duyarlar ve bu, hesaplama maliyetini artırabilir. Temel fikir, her eğitim örneğinin pozitif örneği ile birlikte rastgele seçilen bir dizi negatif örneğin birleştirilmesidir. Model, doğru kelimeyi doğru tahmin etmek için olumlu örnekler üzerinde eğitilirken, yanlış tahminleri yapabilmek için negatif örnekler üzerinde de eğitilir. Bu, modelin daha genel bir bağlamda daha iyi öğrenmesini sağlar.

```python
from gensim.models import Word2Vec
from gensim.models.word2vec import LineSentence
from gensim.models.callbacks import CallbackAny2Vec

# Eğitim veri setinin yolu
data_path = "data.txt"

# Eğitim veri setini yükleme
sentences = LineSentence(data_path)

model = Word2Vec(
    sentences,
    sg=1,  # Skip-gram modeli kullan
    window=5,  # İlgili kelimenin bağlamını belirlemek için kullanılacak kelime penceresinin boyutu
    negative=5,  # Negative sampling için kullanılacak negatif örnek sayısı
    workers=4,  # Paralel işlemler için kullanılacak işçi sayısı
    callbacks=[loss_log]  # Eğitim sırasında kayıp bilgisini göstermek için geri çağırma işlevi
)

# Modeli kaydetme
model.save("word2vec_model")
```

