Bir veri setindeki gizli yapıyı öğrenmek ve ardından veriyi bu gizli yapıyı kullanarak yeniden oluşturmak için kullanılır. Bu işlem, veri sıkıştırma ve ardından sıkıştırılmış veriden orijinal veriyi geri oluşturma olarak düşünülebilir. Bir autoencoder, genellikle iki bölümden oluşur:
- **Encoder (Kodlayıcı):** Giriş verisini daha düşük boyutlu bir temsile dönüştüren kısmıdır.
- **Decoder (Çözücü):** Kodlayıcı tarafından oluşturulan kodu alır ve orijinal giriş verisini yeniden oluşturmak için kullanır. 

**Çalışma Adımları**
Giriş veri bir vektör olarak temsil edilir. Encoder ağı, bu giriş veriyi alan ve daha düşük boyutlu bir kod temsilini dönüştüren bir dizi katmandan oluşur. Her katman, giriş verisini daha soyut ve düşük boyutlu bir şekilde temsil eden özellikler çıkarır. Encoder ve Decoder ağları arasında bir Bottleneck (darboğaz) katmanı bulunur. Bottleneck katmanı, elde edilecek kodun büyüklüğünü (ne kadar sıkıştırma yapılacağını) belirler. Bottleneck katmanının çıktısı, kod veya latent vector olarak adlandırılan daha küçük boyutlu bir vektördür. Bu kod, giriş verisinin temsilidir. Decoder ağı, kodu alır ve orijinal giriş verisini yeniden oluşturmak için kullanılır. Decoder, kodu daha yüksek boyutlu bir vektöre dönüştürür ve orijinal giriş verisinin yapılandırılmasını sağlar. Autoencoder'in eğitimi, yeniden yapılandırılan çıktının orijinal girişe ne kadar yakın olduğunu ölçen bir kayıp fonksiyonunu minimize etmeye dayanır. 

**Sıkıştırma Türleri**
- **Kayıplı Sıkıştırma (Lossy Compression):** Kayıplı sıkıştırma, veri boyutunu azaltırken orijinal verinin tam olarak yeniden elde edilememesi anlamına gelir. Bu, sıkıştırma esnasında bazı bilgilerin kaybolacağı anlamına gelir. Autoencoder'lar kayıplı sıkıştırmayı kullanır. Veriyi en az kayıpla sıkıştıracak şekilde eğitilir. Veriyi kayıpsız olarak sıkıştırma teorik olarak mümkün olsa da bu hep kullanım amacına aykırıdır hem de verimliliğinin azalmasına ve overfitting problemlerine neden olur. 
- **Kayıpsız Sıkıştırma (Lossless Compression):** Kayıpsız sıkılaştırma, veri boyutunu azaltırken orijinal veriyi tam olarak yeniden elde edebilme yeteneği sağlar. Bu, sıkıştırma esnasından hiçbir bilginin kaybolmayacağı anlamına gelir.

**Kullanım Alanları**
- **Feature Extraction (Özellik Çıkarma):** Autoencoder'lar verideki en önemli noktaları tuttukları için özellik çıkarımında kullanılabilirler.
- **Dimension Reduction (Boyut Azaltma):** Temel amacı bu işlemdir.
- **Denoising (Gürültü Azaltma)**
- **Anomali Tespiti**
- **Yeni Veri Üretme**
- **Resim Tamamlama veya Renklendirme**

**Türleri**
- **Vanilla Autoencoder**: Temel ve basit formdaki autoencoder türüdür. "Vanilla", temel anlamına gelir. Bu basit mimari genellikle tam bağlı (fully connected) katmanlardan oluşur.
- **Denoising Autoencoder**: Veri setindeki gürültüyü temizlemek için kullanılır. Gürültülü bir giriş verisi alır ve bu gürültülü veriyi gürültüsüz orijinal veriye daha yakın bir temsil ile yeniden oluşturmayı amaçlar. 
- **Convolutional Autoencoder**: CNN mimarisinden esinlenerek tasarlanıştır. Encoder, convolutional katmanlar kullanarak giriş verisini işler. Convolutional Encoder, üretilen özellik haritalarını düzleştirerek ve daha sonra tam bağlantılı katmanlar kullanarak bir kod temsili oluşturur. Convolutional Decoder, tam bağlantılı katmanlar ve ters konvolüsyonel (deconv) katmanmları kullanarak kodu daha yüksek boyutlu bir vektöre dönüştürür ve orijinal giriş verisini yeniden yapılandırır.
- **Variational Autoencoder**: İstatistiksel ve generative bir autoencoder türüdür. VAE, diğer autoencoder türlerinden farklı olarak, verinin latent uzayında bir olasılık dağılımını öğrenir ve bu dağılımdan örnekler çıkararak yeni veri örnekleri üretme yeteneğine sahiptir. VAE'de encoder çıktısı bir kod değil giriş verisini temsil eden bir ortalama vektörü ve varyans vektörüdür. Encoder, bu vektörleri ürettikten sonra bu dağılıma göre bir nokta seçmek için bir örnekleme işlemi gerçekleştirilir. Decoder, örnekleme işleminden elde edilen noktayı alır ve orijinal giriş verisini yeniden oluşturmak için kullanılır. VAE'nin kayıp fonksiyonu Kullback-Leibler (KL) Divergence içerir. KL Divergence, iki olasılık dağılımı arasındaki farkı ölçer. Model tarafından öğrenilen olasılık dağılımının gerçek veri dağılımına ne kadar yakın olduğunu değerlendirmek için kullanılır.
- **Recurrent Autoencoder**: Zaman serisi veri setleriyle kullanılır. Giriş verisinin zaman bağlamını koruyarak sıkıştırma ve yeniden yapılandırma işlemlerini gerçekleştirir. 
- **Sparse Autoencoder**: Giriş verisindeki özelliklerin daha az sayıda nöron tarafından temsil edilmesini sağlar. Giriş verisindeki özelliklerin özünü daha etkin bir şekilde temsil etmesini ve gereksiz özelliklerin bastırılmasını amaçlar. Sparse regularizasyon içerir.
- **Contractive Autoencoder**: Giriş verisini daha küçük boyutlu bir kod temsiline sıkıştırırken, veri uzayındaki konumları birleştirir ve bu sayede modelin giriş verisinin çeşitli varyasyonlarına karşı daha dirençli hale gelmesini sağlar. Contractive regularizasyon içerir.
- **Fully Connected Autoencoder:** Giriş verisini düzleştirerek ve tam bağlantılı katmanlar aracılığıyla sıkıştırma ve yeniden yapılandırma işlemlerini gerçekleştirir. Diğer autoencoder türlerinden farkı, özellikle görüntü verileri gibi yapısal verilerle çalışırken, zaman serileri veya metin verileri gibi veri yapılarını işlemek için tekrarlayan katmanlar gibi özel yapıları içermez.
