Bir sözcüğü veya bir kategorik değişkeni vektör temsilinde kodlar. Önceden belirlenmiş bir boyuta sahip bir vektörü, giriş olarak alınan değerlerin gömülmesi için kullanılır. Bu işlem, girdi olarak alınan değişkeni bir vektör uzayında temsil eder.

# Parametreler

| Parametre | Açıklama |
| ---- | ---- |
| input_dim | Kelime dağarcığının boyutu.  |
| output_dim | Embedding vektörlerinin boyutu. Genellikle 50-300 (glove.6B.300d, glove.6B.100d gibi) boyutları arasında tercih edilir. Daha büyük boyutlar daha fazla bilgi taşıyabilir fakat hesaplama maaliyetini artırır. |
| input_length | Girdi dizileri sabit bir uzunluğa sahipse kullanılır. |
