2012'de ImageNet ILSVRC (Büyük Ölçekli Görsel Tanıma Yarışması)'de sunuldu. Alex Krizhevsky, Ilya Sutskever ve Geoffrey Hinton tarafından geliştirilmiştir. 5 convolutional  ve 3 tane fully-connected katmandan oluşur. Aktivasyon olarak ReLU kullanır. İki paralel ağ şeklinde çalışır.  AlexNet'in önceki CNN türlerinden farkı;
- ReLU, önceki modellerde kullanılan tanh fonksiyonundan daha hızlı olduğundan eğitim süresini azaltmak için kullanılmıştır. Ayrıca ReLU etkinliğini sınırlamak için Local Response Normalization kullanılmıştır.
- Ezberlemeyi önlemek için seyreltme teknikleri uygulanmıştır.
- Data Augmentation yapılmıştır.

| Katman | Layer | Size | Filter | Kernel Size | Stride | Padding |
| - | - | - | - | - | - | - |
| 0 | Input | 224x224x3 | - | - |  - | - | - |
| 1 | Convolution | 54x54x96 | 11x11 | 96 | 4 | 2 |
| 2 | ReLU | 54x54x96 | - | - | - | - |
| 3 | Max Pooling | 27x27x96 | 3x3 |   
| 4 | LRN |
| 5 | Convolution | 27x27x256 | 
| 6 | ReLU | 27x27x256 |
| 7 | Max Pooling | 13x13x256 | 
| 8 | LRN |
| 9 | Convolution | 13x13x384 | 3x3 | 384 | 1 | 0
| 10 | ReLU | 13x13x384 | - | - | - |  -  |
| 11 | Convolution |  13x13x384 | 3x3 | 384 | 1 | 0
| 12 | ReLU | 13x13x384
| 13 | Convolution | 13x13x256 | 3x3 | 256 | 1 | 0
| 14 | ReLU | 13x13x256 | - | - | - |
| 15 | Max Pooling | 6x6x256 | 3x3 | - | 2 | - |
| 16 | Flatten | 1x1x9216 |
| 17 | FC | 1x1x4096 |
| 18 | ReLU | 1x1x4096 | 
| 19 | Dropout | 1x1x4096 |
| 20 | FC | 1x1x4096 |
| 21 | ReLU | 1x1x4096 |
| 22 | Dropout | 1x1x1000 |
| 23 | FC | 1x1x1000 |
| 24 | Softmax | 1x1x1000 | 

```python
model = Sequential([
	Conv2D(96, kernel_size=(11, 11), strides=4, padding="valid", activation="relu", input_shape=input_shape),
	MaxPooling2D(pool_size=(3, 3), strides=(2, 2), padding="valid", data_format=None)

	Conv2D(256, kernel_size=(5, 5), strides=1, padding="same", activation="relu", kernel_initializer="he_normal")
	MaxPooling2D(pool_size=(3, 3), strides=(2, 2), padding="valid", data_format=None)

	Conv2D(384, kernel_size=(3, 3), strides=1, padding="same", activation="relu", kernel_initializer="he_normal")
	Conv2D(384, kernel_size=(3, 3), strides=1, padding="same", activation="relu", kernel_initializer="he_normal")
	Conv2D(256, kernel_size=(3, 3), strides=1, padding="same", activation="relu", kernel_initializer="he_normal")

	MaxPooling2D(pool_size=(3, 3), strides=(2, 2), padding="valid", data_format=None)

	Flatten(),

	Dense(4096, activation="relu")
	Dense(4096, activation="relu")
	Dense(1000, activation="relu")
	Dense(num_classes, activation="softmax")
])
```