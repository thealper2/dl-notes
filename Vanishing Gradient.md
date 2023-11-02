Patlayan gradyanların tersidir. Gradyanların çok küçük hale geldiği bir durumu ifade eder.

**Ortaya Çıkışı**
- Sigmoid veya tanh gibi bazı aktivasyon fonksiyonları, belirli aralıklarda gradyanları çok küçültme eğilimindedir.
- Derin modeller, daha fazla katmandan oluştuğu için patlayan gradyanlar görülme olasılığı daha yüksektir.
- RNN gibi yapılar, uzun süreli bağlantılar içerdiğinde, gradyanların küçülmesine yol açabilir.

Engelleme Yöntemleri
- Weight İnitalization: Ağırlıkların rastgele başlatılması (He veya Xavier initialization...) vanishing gradient oluşma olasılığını azaltabilir.
- Gradient Clipping: Gradyanlar, belirli bir eşik değerden büyükse kırpılır.
- Skip Connections: 