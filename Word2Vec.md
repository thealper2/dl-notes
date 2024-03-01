Bir kelimeyi vektörlerle temsil etmek için kullanılır. İki farklı yöntemi içerir:
- **Skip-gram:** Orta kelimeyi alarak çevresindeki kelimeleri tahmin etme. Belirli bir kelimenin etrafındaki bağlamı tahmin etmek için kullanılır. Bu yöntemde, bir kelimenin bağlamındaki diğer kelimeler, o kelimenin vektörlerinin güncellenmesinde kullanılır. Pencere büyüklüğü çevreden kaç kelime alınacağını gösterir. Örneğin 2 ise ortadaki kelimenin sağından 2 solundan 2 kelime alınır. CBOW'a göre daha fazla hesaplama gücü gerektirir. 
```css
\max \prod_{t=1}^{T} P(w_{t+j} | w_t)

T, eğitim setindeki toplam kelime çifti sayısı
j, kelimenin etrafındaki bağlamın boyutu
P(w_t+j | wt), wt kelimesinin bağlamındaki wt+j kelimesinin olasılığı
```
- **Continious Bag of Words (CBOW):** Çevredeki kelimelerden ortadaki kelimeyi tahmin etme. Belirli bir kelimenin verilen bir bağlamdaki olasılığını tahmin etmek için kullanılır. Bu yöntemde bir kelimenin vektörü o kelimenin bağlamındaki diğer kelimelerin vektörleri kullanılarak tahmin edilir. Skip-gram'a göre daha az hesaplama gücü gerektirir. Küçük veri setleri için uygundur.
```css
\max \prod_{w \in C} P(w | w_i)

C, bağlamdaki kelime kümesi
P(w|wi), wi kelimesinin bağlamındaki diğer kelimelerden w kelimesinin olasılığı
```

```python
from gensim.models import Word2Vec

# Örnek bir metin corpus
corpus = [["bu", "bir", "örnek", "cümle"], ["başka", "bir", "örnek"]]

# GloVe modelini oluştur
model = Word2Vec(corpus, vector_size=100, window=5, min_count=1, sg=1)

# Kelime vektörlerini al
word_vectors = model.wv

# Örnek bir kelimenin vektörünü al
vector = word_vectors['örnek']
print("Kelime vektörü:", vector)
```