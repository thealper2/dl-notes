LSTM (Uzun Kısa Süreli Bellek), önceki zaman adımlarından gelen bilgileri hatırlama ve uzun vadeli bağımlılıkları modelleme yeteneğine sahiptir. LSTM, RNN'in kısa vadeli bellek problemini çözmek için oluşturulmuştur. LSTM Cell State, Forget Gate, Input Gate ve Output Gate'den oluşur. Cell State, bilgileri hücreler boyunca taşıyan bir iletim hattıdır. Taşınması gereken bilgiler kapılar ile belirlenir. Kapılarda, sigmoid fonksiyonunu kullanarak 0 olan bilgileri unutur ve 1 olan bilgiler ilerlemeye devam eder.
- **Forget Gate**: Bilgilerin unutulup unutulmayacağına karar veren kapıdır. Bilgiler sigmoid fonksiyonuna sokulur. 0 olan bilgiler unutulur. 1 olanlar taşınmaya devam eder.
- **Input Gate:** Cell State'i günceller. Sigmoid fonksiyonu ile 0 olan bilgiler önemsiz 1 olan bilgiler önemli olarak kabul edilir. Düzenleme işlemi için tanh kullanılır. Daha sonra sigmoid ve tanh sonuçları çarpılır ve bilginin güncellenip güncellenmeyeceğine karar verilir.
- **Output Gate:** Bir sonraki hücrenin girişini belirler. Tahmin yapmak için kullanılır.