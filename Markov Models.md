Markov modelleri, Markov zinciri adı verilen ve gelecekteki durumun yalnızca mevcut duruma bağlı olduğu bir süreç modellemesi türünü temsil eder. Bu model, geçmiş durumların gelecekteki durumları belirlemede tam olarak yeterli olduğunu varsayar. Bu, bir durumun gelecekteki olasılığını, yalnızca mevcut durumun bilgisine dayanarak tahmin etmek için kullanılır. Markov zincirleri, durumları temsil eden bir durum uzayı ve durumlar arasındaki geçiş olasılıklarını tanımlayan bir geçiş matrisi kullanır. Her bir durum, bir durum uzayının bir noktasını temsil eder ve geçiş matrisi, her bir durumun diğer durumlara geçiş olasılıklarını belirtir. Türleri:
- Birinci Dereceden Markov Zinciri
- Yüksek Dereceden Markov Zinciri
- Gizli Markov Modeli (Hidden Markov Model HMM)

---
# Birinci Dereceden Markov Zinciri
Gelecekteki durum, yalnızca mevcut duruma bağlıdır. Bir sonraki durum, yalnızca mevcut durumun bilgisine dayanarak tahmin edilir.

**Çalışma Adımları**
1. Modelin kullanılacağı durumlar tanımlanır.
2. Her bir durumun, bir sonraki duruma geçme olasılığı belirlenir.
3. Modelin başlangıç durumu (başlangıç noktası) seçilir.
4. Başlangıç durumundan başlayarak, her bir adımda geçiş olasılıklarına dayanarak bir sonraki durum rastgele seçilir.
5. Zincir belirlenen adımlar boyunca çalıştırılır ve bir sonraki durum tahmin edilir.

```css
P(X_{n+1} = s_j | X_n = s_i) = P_{ij}

P_{ij}, geçiş olasılığını ifade eden bir olasılık matrisinin elemanıdır
P(X_{n+1} = s_j | X_n = s_i), durum si'den durum sj' ye geçişin olasılığı
```

```python
import markovify

# Örnek metin
text = """
Bu bir örnek metin. Bu metin birinci dereceden Markov zinciri ile analiz edilecek. 
Markov zincirleri, geçmiş duruma bağlı olarak bir sonraki durumu tahmin etmek için kullanılır.
"""

# Markov zinciri modelini oluşturma
model = markovify.Text(text, state_size=1)

# Rastgele bir dizi oluşturma
generated_sequence = model.make_sentence()

print("Generated Sequence:", generated_sequence)
```

---
# Yüksek Dereceden Markov Zinciri
Yüksek dereceden Markov zinciri, birinci derecede Markov zincirinden farklı olarak, daha önceki birden fazla durumu dikkate alarak bir sonraki durumu tahmin etmek için kullanılır. Geçmişteki birden fazla durumun etkilerini içeren daha karmaşık ilişkileri modelleyebilir. 

```python
import markovify

# Örnek metin
text = """
Bu bir örnek metin. Bu metin yüksek dereceden Markov zinciri ile analiz edilecek. 
Yüksek dereceden Markov zincirleri, geçmiş duruma bağlı olarak bir sonraki durumu tahmin etmek için kullanılır.
"""

# Yüksek dereceden Markov zinciri modelini oluşturma
model = markovify.Text(text, state_size=2)  # state_size parametresi, yüksek dereceden zincirin boyutunu belirtir

# Rastgele bir dizi oluşturma
generated_sequence = model.make_sentence()

print("Generated Sequence:", generated_sequence)
```

```css
P(X_{n+1} = s_j | X_n = s_i, X_{n-1} = s_k, ..., X_{n-d} = s_l) = P_{ijkl...l}
```

---
# Hidden Markov Model
Zamanla değişen gizli durumların gözlemlenebilir durumlar aracılığıyla modellendiği bir olasılıksal modeldir. HMM, bir Markov zincirinin gizli bir durumla eşlenmesiyle oluşturulur ve bu gizli durumlar gözlemlenebilir durumlarla ilişkilendirilir. İki tür durumu içerir:
- **Gizli Durumlar (Hidden States):** Gözlemleyiciler tarafından doğrudan gözlemlenemeyen ve model tarafından tahmin edilmeye çalışılan durumlardır. 
- **Gözlemlenebilir Durumlar (Observable States):** Model tarafından gözlemlenebilen durumlardır. Bu durumlar gizli durumlarla ilişkilendirilir ve belirli bir zaman aralığında gözlenen gerçek verilerdir.

**Çalışma Adımları**
1. Modelin kullanacağı gizli ve gözlemlenebilir durumlar tanımlanır.
2. Gizli durumlar arasındaki geçiş olasılıkları belirlenir.
3. Her bir gizli durumun gözlemlenebilir durumlarla ilişkilendirilme olasılıkları belirlenir.
4. Modelin başlangıç durumu belirlenir.
5. Model genellikle gözlemlenen veriler kullanılarak eğitilir. Bu, Viterbi algoritması veya Baum-Welch algoritması gibi yöntemler kullanılarak gerçekleştirilebilir.

```css
P(Y_1=y_1, Y_2=y_2, ..., Y_n=y_n, X_1=x_1, X_2=x_2, ..., X_n=x_n) = P(X_1) \cdot P(Y_1|X_1) \cdot \prod_{t=2}^{n} P(X_t|X_{t-1}) \cdot P(Y_t|X_t)

Yn, gözlemlenebilir durumları
Xn, gizli durumları
P(X1) başlangıç durumunun olasılığını
P(Yt|Xt) gözlemlenebilir durumların gizli durumlar altında koşulluk olasılıklarını
P(Xt|Xt-1) gizli durumların birbirine geçiş olasılıklarını
```

```python
from hmmlearn import hmm
import numpy as np

# Örnek veri
X = np.array([[0], [1], [0], [1], [0], [1], [0], [1]])
lengths = [8]  # Gözlemlenen verinin uzunluğu

# Gizli Markov Modeli oluşturma
model = hmm.GaussianHMM(n_components=2, covariance_type="full")

# Modeli eğitme
model.fit(X, lengths)

# Gizli durumları tahmin etme
predicted_states = model.predict(X)

print("Gizli Durumlar:", predicted_states)
```