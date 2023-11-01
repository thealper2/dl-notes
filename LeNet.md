ilk olarak 1996 yılında Yann LeCun tarafından CNN bir makale şeklinde yayınlandı. 1998 yılında ilk uygulaması yine Yann LeCun ve ekibi tarafından posta numaraları, banka çekleri üzerindeki sayıların okunması için geliştirildi. Yann Lecun, ağın ismine "LeNet" adını vermiştir. Bu modelde boyut azaltma adımlarında max pooling yerine average pooling işlemi yapılmaktadır. Aktivasyon fonksiyonu olarak sigmoid ve hiperbolik tanjant kullanılmaktadır. Çıkışında softmax bulunmaktadır. 60 bin parametre hesaplanır. Ağ boyunca girdinin yükseklik ve genişlik bilgisi azalır ve derinlik değeri artmaktadır.

| Katman | Layer | Size | Feature Map | Filter | Stride |
| - | - | - | - | - | - |
| 0 | Input | 32x32x3 | - |  - | - |
| 1 | Convolution (Evrişim) | 28x28x108 | 6 | 5x5 | 1 |
| 2 | ReLU | 28x28x108 | - | - | - |
| 3 | Average Pooling (Havuzlama) | 14x14x108 | 6 | 2x2 | 2 |
| 4 | Convolution (Evrişim) | 10x10x108 | 16 | 5x5 | 1 |
| 5 | ReLU | 10x10x108 | - | - | - |
| 6 | Average Pooling (Havuzlama) | 5x5x108 | 16 | 2x2 | 2 |
| 7 | FC | 1x1x100 | - | - | - |
| 8 | ReLU | 1x1x100 | - | - | - |
| 9 | FC | 1x1x100 | - | - | - |
| 10 | ReLU | 1x1x100 | - | - | - |
| 11 | FC | 1x1x43 | - | - | - |
| 12 | Softmax | 1x1x43 | - | - | - |

```python
model = Sequential([
    # 32 - 5 + 1 = 28
    # (28, 28, 6)
    Conv2D(6, kernel_size = (5, 5), activation = "relu", input_shape = (28, 28, 1)),
    # (28, 28, 6) / (2, 2) = (14, 14, 6)
    MaxPooling2D(pool_size = (2, 2)),
    # 14 - 5 + 1 = 10
    # (10, 10, 6)
    Conv2D(16, kernel_size = (5, 5), activation = "relu"),
    # (10, 10, 16) / (2, 2) = (5, 5, 16)
    MaxPooling2D(pool_size = (2, 2)),
    Flatten(),
    Dense(120, activation = "relu"),
    Dense(84, activation = "relu"),
    Dense(10, activation = "softmax")
])
```
