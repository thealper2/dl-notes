Non-negative Matrix Factorization (NMF), çok değişkenli verilerde kullanılan bir matris faktörizasyon tekniğidir. NMF, bir veri matrisini iki veya daha fazla alt matrise çözer. Bu faktörizasyon, orijinal matrisi daha küçük boyutlu ve daha yorumlanabilir alt matrislere bölerek veri içindeki gizli yapıları keşfetmeyi amaçlar. Temel amacı, veri matrisindeki her bir özelliği temsil eden bazı temel özelliklerin kombinasyonunu bulmaktır.


```python
from sklearn.decomposition import NMF
import numpy as np

# Örnek veri oluşturma
X = np.array([[1, 1, 1], [2, 2, 2], [3, 3, 3], [4, 4, 4]])

# NMF modelini tanımlama ve eğitme
num_components = 2  # Alt matrislerin sayısı
nmf_model = NMF(n_components=num_components, init='random', random_state=42)
W = nmf_model.fit_transform(X)  # Birinci alt matris
H = nmf_model.components_  # İkinci alt matris

# Oluşturulan alt matrislerin görselleştirilmesi
print("W matrix:")
print(W)
print("H matrix:")
print(H)
```