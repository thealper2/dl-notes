Federated Learning, merkezi olmayan bir öğrenme yöntemidir. Bir modelin birden fazla cihazda eğitilmesini sağlar. Modeller uç cihazlarda eğitilir ve güncellenen parametreler merkezi bir sunucuya gönderilir. Böylece veri güvenliği sağlanır.

**Çalışma Adımları**
1. Merkezi sunucu tarafından bir model oluşturulur.
2. Eğitim verileri uç cihazlara dağıtılır. Her cihaz kendi verileri ile modeli eğitir.
3. Güncellenen parametreler merkezi sunucuya gönderilir.
4. Gelen parametreler ile merkezi sunucudaki model güncellenir.
5. Güncellenen model tekrar uç cihazlara dağıtılır ve işlem tekrarlanır. 