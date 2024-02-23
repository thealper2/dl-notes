**Conv1D:** 1 boyutlu konvolüsyon işlemi uygulamak için kullanılan bir katmandır. Giriş verileri üzerinde belirli bir pencere boyutunda kaydırılan bir filtre (kernel) uygular. Bu filtre, giriş verilerini bir boyutlu konvolüsyon işleminden geçirir ve çıktı olarak konvolüsyon sonuçlarını verir. Genellikle zamansal verilerin işlenmesi, sıralı verilerin analizi gibi durumlarda kullanılır.
**Conv2D:** 2 boyutlu konvolüsyon işlemi uygulamak için kullanılan bir katmandır. Giriş verileri üzerinde belirli bir pencere boyutunda kaydırılan bir filtre (kernel) uygular. Bu filtre, giriş verilerini iki boyutlu konvolüsyon işleminden geçirir ve çıktı olarak konvolüsyon sonuçlarını verir. Genellikle görüntü işleme gibi iki boyutlu verilerin işlenmesi durumlarda kullanılır.
**Conv3D:** 3 boyutlu konvolüsyon işlemi uygulamak için kullanılan bir katmandır. Giriş verileri üzerinde belirli bir pencere boyutunda kaydırılan bir filtre (kernel) uygular. Bu filtre, giriş verilerini üç boyutlu konvolüsyon işleminden geçirir ve çıktı olarak konvolüsyon sonuçlarını verir. Genellikle video işleme, 3D görüntü verileri gibi üç boyutlu verilerin işlenmesi durumlarda kullanılır.

# Parametreler

| Parametre | Açıklama |
| ---- | ---- |
| filters | Çıkış uzayının boyutu. |
| kernel_size | Filtre boyutu. |
| stride | Kaydırma adımı |
| padding | Giriş boyutunu ayarlamak için kullanılcak yöntem. |
| activation | Aktivasyon fonksiyonu. |
