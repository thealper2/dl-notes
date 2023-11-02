**Ortaya Çıkışı**
- Backpropagation sırasında, gradyan çok küçük veya çok büyükse, ağın ağırlıkları doğru bir şekilde güncellenemez.
- Sigmoid veya tanh gibi bazı aktivasyon fonksiyonları, belirli aralıklarda gradyanları çok küçültme eğilimindedir.
- Derin modeller, daha fazla katmandan oluştuğu için patlayan gradyanlar görülme olasılığı daha yüksektir.
### Engelleme Yöntemleri
- Weight İnitalization: Ağırlıkların rastgele başlatılması (He veya Xavier initialization...) patlayan gradyanların oluşma olasılığını azaltabilir.
- Gradient Clipping: Gradyanlar, belirli bir eşik değerden büyükse kırpılır.
- Adaptive Optimizer
- Batch Normalization