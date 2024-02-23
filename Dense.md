Tam bağlı olarak da adlandırılır, çünkü her bir giriş düğümünün her bir çıkış düğümüyle bağlantılı olduğu bir katmandır. Dense katmanının çıkışı, giriş verileri (x) ve ağırlıkları (W) ile bias (b) terimlerinin matris çarpımının sonucu olarak hesaplanır ve ardından bir aktivasyon fonksiyonuna geçirilir.

```shell
Çıkış = AktivasyonFonksiyonu(W * x + b)
x => Giriş
b => Bias
W => Ağırlık

1. Önce giriş verileri ile ağırlıklar çarpılır.
2. Elde edilen sonuca bias eklenir.
3. Sonuç bir aktivasyon fonksiyonundan geçirilir ve çıkış üretilir.
```

# Parametreler

| Parametre | Açıklama |
| ---- | ---- |
| units | Katmandaki gizli nöron sayısıdır yani çıkış boyutunu belirtir. Ağın karmaşıklığını belirler. Daha fazla nöron, öğrenme yeteneğini artırabilir fakat overfitting riskini de artırabilir. |
| activation | Kullanılacak aktivasyon fonksiyonu. Eğer herhangi bir şey belirtilmezse aktivasyon uygulanmaz. |
| use_bias | Bias kullanıp kullanmayacağını belirtir. |
| kernel_initializer | Ağırlıkların başlangıç değerlerini belirtir. |
| bias_initializer | Bias'ın başlangıç değerini belirtir. |
| activity_regularizer | Çıktı üzerindeki düzenleyici. |
| kernel_constraint | Ağırlıklar üzerinde uygulanacak sınırlayıcı. |
| bias_constraint | Bias üzerinde uygulanacak sınırlayıcı. |
| bias_regularizer | Bias üzerindeki düzenleyici. |
| kernel_regularized | Kernel üzerindeki düzenleyici. |
