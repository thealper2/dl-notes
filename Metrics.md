# Accuracy Metrics

Sparse ile Normal metrik arasındaki fark:
- Sparse'de tahminler one-hot encode edilmemiş şekilde oluşacaktır.
- Normal'de tahminler one-hot encode edilmiş şekilde oluşacaktır.

```python
Sparse = [2]
Normal = [0 0 1 0]
```

- Accuracy: Bir ikili/çoklu sınıflandırma modelinde doğru sınıflandırılan örneklerin oranını ölçen bir metriktir. Doğru tahmin edilen etiket sayısının toplam örnek sayısına bölünmesiyle elde edilir. 

```python
from keras.metrics import Accuracy
model.compile(optimizer='adam', loss='binary_crossentropy', metrics=[Accuracy()])
```

- BinaryAccuracy: Accuracy tüm sınıfların doğru şekilde sınıflandırılma oranını ölçer, BinaryAccuracy ise yalnızca iki sınıf arasında doğru şekilde sınıflandırılan örneklerin oranını ölçer.

```python
from keras.metrics import BinaryAccuracy
model.compile(optimizer='adam', loss='binary_crossentropy', metrics=[BinaryAccuracy()])
```

- CategoricalAccuracy:

```python
from keras.metrics import CategoricalAccuracy
model.compile(optimizer='adam', loss='categorical_crossentropy', metrics=[CategoricalAccuracy()])
```

- SparseCategoricalAccuracy

```python
from keras.metrics import SparseCategoricalAccuracy
model.compile(optimizer='adam', loss='sparse_categorical_crossentropy', metrics=[SparseCategoricalAccuracy()])
```

- TopKCategoricalAccuracy: Modelin doğru etiketleme yapması için belirli bir sıra k değerine göre doğru tahmin oranını ölçer. Yani, modelin en yüksek k olasılığa sahip sınıfları doğru tahmin etme yeteneğini ölçer. k=1 ise "CategoricalAccuracy" metriği gibi işlev görür.

```python
from keras.metrics import TopKAccuracy
model.compile(optimizer='adam', loss='categorical_crossentropy', metrics=[TopKAccuracy(k=5)])
```

- SparseTopKCategoricalAccuray

```python
from keras.metrics import SparseTopKAccuracy
model.compile(optimizer='adam', loss='sparse_categorical_crossentropy', metrics=[SparseTopKAccuracy(k=5)])
```

---
# Probabilistic Metrics

- BinaryCrossentropy

```shell
−1/N​∑(i=1)(N) ​(yi​ * log(y^​i​) + (1−yi​) * log(1−y^​i​))
# N => Toplam örnek sayısı
# yi => Gerçek etiketler
# y^i => Tahmin edilen etiketler
```

```python
from keras.metrics import BinaryCrossentropy
model.compile(optimizer='adam', loss='mse', metrics=[BinaryCrossentropy()])
```

- CategoricalCrossentropy

```shell
−1/N​∑(i=1)(N) ∑(j=1)(C) yij * log(y^ij)
# N => Toplam örnek sayısı
# C => Toplam sınıf sayısı
# yij => Gerçek etiketler
# y^ij => Tahmin edilen etiketler
```

```python
from keras.metrics import CategoricalCrossentropy
model.compile(optimizer='adam', loss='mse', metrics=[CategoricalCrossentropy()])
```

- SparseCategoricalCrossentropy

```shell
−1/N​∑(i=1)(N) log(y^iyi)
# N => Toplam örnek sayısı
# y^iyi => Tahmin edilen etiketlerin olasılık dağılımı
```

```python
from keras.metrics import SparseCategoricalCrossentropy
model.compile(optimizer='adam', loss='mse', metrics=[SparseCategoricalCrossentropy()])
```

- KLDivergence: İki olasılık dağılımı arasındaki farkı ölçer.

```shell
KLDivergence(P ∣∣ Q) = ∑(i)​ P(i) * log(Q(i) / P(i)​)
```

```python
from keras.metrics import KLDivergence
model.compile(optimizer='adam', loss='mse', metrics=[KLDivergence()])
```

- Poisson

```shell
Poisson(y, y^) = y^ - y * log(y^)
# y = > Gerçek değer
# y^ => Tahmin edilen değer
```

```python
from keras.metrics import Poisson
model.compile(optimizer='adam', loss='mse', metrics=[Poisson()])
```

---
# Regression Metrics

- MeanSquaredError

```shell
1/N ​∑(i=1)(N) = ​(yi​ − y^​i​) ^ 2
# N => Toplam örnek sayısı
# yi => Gerçek değer
# y^i => Tahmin edilen değer
```

- RootMeanSquaredError

```shell
square(RMSE)
sqrt(mean((y_pred - y_true) ** 2))
```

- MeanAbsoluteError

```shell
  1 / N ​∑ (i=1)(N) ​∣ yi​ − y^​i ​∣

mean(abs(y_true - y_pred))
```

- MeanAbsolutePercentageError

```shell
100 * mean(abs((y_yrue - y_pred) / y_true))
```

- MeanSquaredLogarithmicError

```shell
1​ / N  ∑(i=1)(N) ​( log(yi​ + 1) − log( y^​i ​+ 1) ) ^ 2
```

- CosineSimilarity

```shell
(a * b) / (||a|| * ||b||)
```

- LogCoshError

```shell
mean(log(cosh(yi - y^i)))
```

