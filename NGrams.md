Ngramlar, bir metin veya serideki ardışık "n" elemanlık gruplardır. Bu gruplar, metindeki belirli bir örüntüyü veya dilbilgisel yapının bir bölümünü temsil eder. N-gram modelinin doğruluğu seçilen n değerine bağlı olarak değişebilir. N-gram olasılıkları kullanılarak bir metin tamamlama yapılabilir. 
- **Uni-gram (1-gram):** Tek bir kelime veya karakteri temsil eder. Her bir kelimenin veya karakterin bağımsız olarak ele alındığı durumlarda faydalıdır.
- **Bi-gram (2-gram):** Ardışık iki kelime veya karakteri temsil eder. Kelimeler arasındaki bağlantıları veya ilişkileri analiz etmek için faydalıdır.
- **Tri-gram (3-gram):** Ardışık üç kelime veya karakteri temsil eder.

```shell
Bir kelimenin başka bir kelimenin ardından gelme olasılığı => birlikte geçme sayısı / ilk kelimenin geçme sayısı
```

```python
import nltk
from nltk.util import ngrams
from nltk.tokenize import word_tokenize

# Örnek metin
text = "Bu bir örnek cümle."

# Metni kelimelere ayır
tokens = word_tokenize(text)

# Bi-gramlar
bi_grams = list(ngrams(tokens, 2))
print("Bi-gramlar:", bi_grams)

# Tri-gramlar
tri_grams = list(ngrams(tokens, 3))
print("Tri-gramlar:", tri_grams)
```

