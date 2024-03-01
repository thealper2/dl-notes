GloVe (Global Vector for Word Representation), bir kelime gömme yöntemidir.  Her bir kelime için vektörel temsiller oluşturur. Bu temsilleri oluştururken, kelimenin bağlamındaki ortaklıkları ve bağlamdaki sıklığını dikkate alır. Bu nedenle, kelimenin anlamını yakalamak için o kelimenin çevresindeki kelimelerin istatistiksel özelliklerini kullanır. Word2Vec'ten farklı olarak word2vec optimizasyon işlemini her seferinde yapar. Glove ise önce kaç defa geçtiğini hesaplar sonra optimizasyonu yapar yani her seferinde değil en sonda yapıyor.

```css
J = \sum_{i,j=1}^{V} f(X_{ij}) \left( w_{i}^{T} \tilde{w_{j}} + b_{i} + \tilde{b_{j}} - \log X_{ij} \right)^2

# J, maliyet fonksiyonu
# V, kelime dağarcığının boyutu
# Xij, kelime i ve kelime j arasındaki ko-çalışma olasığı (kelime i ve j çiftinin birlikte geçme sayısı)
# wi ve W^j kelime vektörleri
# bi ve b^j bias terimleri
# f, ağırlık fonksiyonu
```

Ağırlık fonksiyonunun gereksinimleri:
- Ağırlık fonksiyonu, iki kelime arasındaki ilişkiyi temsil etmek için skaler bir değer üretmelidir. Bu skaler değer, kelime vektörlerinin iç çarpımı ile hesaplanır ve iki kelime arasındaki ko-çalışma olasılığını yansıtmalıdır.
- Ağırlık fonksiyonu, iki kelime arasındaki ilişkinin yönünü yansıtmalıdır. Yani, kelime Xi kelime Xj 'nin ko-çalışma olasılığına katkıda bulunuyorsa, aynı oranda kelime Xj kelime Xi 'nin ko-çalışma olasılığına katkıda bulunmamalıdır.
- Ağırlık fonksiyonu, bir kelime kendi kendisiyle olan ilişkiyi temsil ettiğinde sıfır değerini vermeli ve maliyet fonksiyonuna herhangi bir katkıda bulunmamalıdır. Yani, Xii​ değeri sıfır olmalıdır.

