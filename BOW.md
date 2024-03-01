BOW (Bag of Words), metindeki kelimelerin frekansına bakarak metinler arasında benzerlik ölçer. Kelime sırasını ve gramer yapılarını dikkate almaz sadece frekansa bakar. Metinlerin uzunluğuna bağlı değildir. BoW, bir metindeki her kelimenin varlığını veya sıklığını temsil eden bir vektör oluşturur. Her kelime, metinde kaç kez geçtiğine veya metinde geçip geçmediğine bağlı olarak bir özellik olarak temsil edilir. Veri setindeki geçen tüm farklı kelimeler için bir sözlük oluşturulur. Her bir metin için, sözlükte her kelimenin sıklığına göre bir vektör oluşturulur.  

```python
from sklearn.feature_extraction.text import CountVectorizer

# Örnek metin veri seti
# dict => [baska, bir, bu, cumle, ornek]
corpus = [
    'Bu bir örnek cümle.', # [1 1 1 0 0]
    'Başka bir örnek cümle.', # [0 1 1 1 0]
    'Bu bir başka örnek cümle.' # [1 1 1 0 1]
]

# CountVectorizer kullanarak BoW vektörlerini oluşturma
vectorizer = CountVectorizer()
X = vectorizer.fit_transform(corpus)

# Oluşturulan BoW matrisini ekrana yazdırma
print("BoW Matrisi:")
print(X.toarray())

# Sözlük (kelimeler) listesini ekrana yazdırma
print("Sözlük (Kelimeler):")
print(vectorizer.get_feature_names())
```