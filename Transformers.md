2017 yılında "Attention is All You Need" adlı bir makalede Google araştırmacıları tarafından tanıtılmıştır.  Seq2Seq modellerinde karşılaşılan bağlam kaybı problemlerine etkili bir çözüm sunar. Bu problemi aşmak için Attention (Dikkat) mekanizmasını kullanır.

**Ana Bileşenler**
1. **Encoder-Decoder Yapısı:** Encoder, girdi verisini içsel temsillere dönüştürür. Decoder, bu içsel temsilleri çıktıya dönüştürür.
2. **Attention Mekanizması:** Modelin belirli bir kelimenin işlenmesi sırasında diğer kelimelere odaklanmasını sağlar. Bu sayede, modelin girdi verisindeki uzak bağlantıları da dikkate alması mümkün olur.
3. **Layer Normalization ve Residual Connections**
4. **Positional Encoding:** Girdi verisindeki kelime sıralamasını koruyabilmek için bir pozisyon kodlaması kullanır.

# Attention Mekanizması
Attention mekanizması, kod çözücü ağının her adımında, her bir giriş kelimesine odaklanmasına izin vererek çalışır. Yani kod çözücü ağı çıkışın her bir kelimesini oluştururken, giriş dizisindeki her bir kelimenin önemini değerlendirir ve çıkışın o kelimeyi üretirken girişin hangi kısımlarına odaklanması gerektiğin karar verir.

# Encoder
Encoder, girdi verisini içsel temsillere dönüştürür. Bunu gerçekleştirmek için encoder bloğu, word embedding, positional encoding, multi-head attention, normalizasyon ve bir dizi lineer katman kullanır.

# Word Embedding
Kelimelerin anlamsal benzerliklerini yansıtacak şekilde gömümlere dönüştürülmesidir. Bu sayede kelimeler anlamsal benzerliklerini koruyarak modelin işleyebileceği sayısal verilere dönüştürülür.

# Positional Encoding
Positional encoding, kelimelerin sıra bilgisini koruyarak sayısal vektörlere dönüştürülmesidir. Bu sayede model kelimeler arası ilişkileri daha iyi anlayabilir. Word embedding işleminden çıkan gömümler ile positional encoding işleminden çıkan vektörler toplanır. Böylece, girdi içerisinde hem anlam bilgisi hem sıra bilgisi barındırılır.

```css
\text{PositionalEncoding}(pos, i) = \begin{cases}
    \sin\left(\frac{pos}{10000^{2i/d_{\text{model}}}}\right) & \text{if } i \text{ is even} \\
    \cos\left(\frac{pos}{10000^{2i/d_{\text{model}}}}\right) & \text{if } i \text{ is odd}
\end{cases}
```

# Multi-Head Attention
Positional encoding katmanından gelen girdi verisi key, value ve query olmak üzere üç farklı kanaldan iletilir ve daha sonra her bir kanalda lineer katmanlardan geçer. 
- **Key:** Key kanalı, dikkat odaklamasının hangi kelimelerin dikkate alınacağını belirlemek için kullanılır. Her bir kelimenin içsel temsili, key kanalı tarafından temsil edilir ve dikkat ağırlıklarının hesaplanmasında kullanılır
- **Query:** Query kanalı, dikkat odaklamasının hangi kelimelere odaklanacağını belirlemek için kullanılır. Her bir kelimenin içsel temsili, query kanalı tarafından temsil edilir ve dikkat ağırlıklarının hesaplanmasında kullanılır.
- **Value:** Value kanalı, dikkat ağırlıklarının hesaplanmasından sonra kullanılarak dikkat odaklamasının sonucu olarak elde edilen temsilin oluşturulmasında kullanılır. Dikkat ağırlıkları ile ağırlıklı olarak çarpılan her bir kelimenin içsel temsili, value kanalı tarafından temsil edilir.

Multi-head attention denmesinin sebebi, positional encoding katmanından gelen veriler birden fazla bloktan geçer ve çıktıları birleştirilir. Son temsili elde etmek için doğrusal olarak dönüştürülür.

# Residual Connections
Residual connections, modelin daha derin hale getirilmesini sağlar ve aşırı öğrenmeyi önler. Bu bağlantılar, bir katmanın girdi verisini alır ve o katmandan çıkan çıktıyı girdi verisi ile toplar. Bu sayede, katmanların doğrudan öğrenmesi gereken bir araç vardır ve gradientlerin daha iyi akması sağlanır.

# Layer Normalization
Layer normalization, her bir katmanın çıktılarını normalize ederek modelin daha kararlı ve tutarlı bir şekilde eğitilmesini sağlar. Bu, her bir katmanın çıktılarının ortalamasını sıfıra merkezlemek ve birim varyans ile ölçeklemek suretiyle gerçekleştirilir.

# Decoder
İlk olarak, başlangıç tokeni decoder'a girdi olarak verilir. Bu başlangıç tokeni, decoder'a çevirilecek cümlenin başlangıcını belirtir. Başlangıç tokeni, self-attention mekanizması kullanılarak işlenir. Bu adımda, başlangıç tokeninin içsel temsili hesaplanır ve diğer kelimelere dikkat edilerek daha karmaşık bir temsil elde edilir. Self-attention adımından sonra, decoder bloğu, encoder bloğundan gelen çıktıları dikkate alır. Bu adımda, encoder-decoder attention mekanizması kullanılarak encoder bloğunun çıktılarına dikkat edilir. Her bir attention adımından sonra, decoder bloğunda layer normalization ve residual bağlantılar kullanılır. Bu teknikler, modelin daha kararlı bir şekilde eğitilmesine ve aşırı öğrenmeyi önlemesine yardımcı olur. Son olarak, her bir attention adımından sonra, decoder bloğunda bir ileri beslemeli sinir ağı (feed-forward neural network) bulunur. Bu ağ, içsel temsilleri daha karmaşık ve yüksek seviyeli bir şekilde işlemek için kullanılır. İleri beslemeli sinir ağı adımından sonra, sonlandırma tokeni decoder'a girdi olarak verilir. Bu sonlandırma tokeni, decoder'ın çıktı oluşturma işlemini sonlandırır ve decoder'ın çıktı dizisini tamamlar.