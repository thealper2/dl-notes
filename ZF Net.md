2013'de ImageNet ILSVRC (Büyük Ölçekli Görsel Tanıma Yarışması)'de sunuldu. Matthew Zeiler ve Rob Fergus tarafından geliştirilmiştir. ZF Net'te, AlexNet'e göre ilk katmandaki filtre boyutu ve adım sayısı küçültülmüş ve orta evrişim katmanları büyütülmüştür. ZF Net'te, öğrenilen bilgiyi görselleştiren ağın her katmanındaki görüntü piksellerine geri beslenen zıt evrişim işlemi (deconvnet) eklenmiştir. Böylece zengin özellikler gözetimsiz olarak çıkarılabilmektedir.

| Katman | Layer | Size | Filter | Kernel Size | Stride | Padding |
| - | - | - | - | - | - | - |
| 0 | Input | 224x224x3 | - | - |  - | - | - |
| 1 | Convolution | 37x37x96 | 7x7 | 96 | 2 | 0 |
| 2 | ReLU | 37x37x96 | - | - | - | - |
| 3 | LRN |   
| 4 | Max Pooling | 37x37x96 | 3x3 | - | 2 | - |
| 5 | Convolution | 17x17x256 | 5x5 | 256 | 1 | 0 |
| 6 | ReLU | 17x17x256 |
| 7 | Max Pooling | 17x17x256 | 3x3 | - | 1 | - |
| 8 | Convolution | 17x17x512 | 3x3 | 512 | 1 | 0 |
| 9 | ReLU | 17x17x512 |
| 10 | Convolution | 17x17x512 | 3x3 | 512 | 1 | 0 |
| 11 | ReLU | 17x17x512 |
| 12 | Convolution | 17x17x512 | 3x3 | 512 | 1 | 0 |
| 13 | ReLU | 17x17x512 |
| 14 | Max Pooling | 17x17x512 | 3x3 | - | 2 | - |
| 15 | Convolution | 6x6x512 | 3x3 | 512 | 1 | 0 |
| 16 | ReLU | 6x6x512 |
| 17 | Flatten |
| 18 | FC | 1x1x4096 |
| 19 | ReLU | 1x1x4096 |
| 20 | Dropout | 
| 21 | FC | 1x1x4096 |
| 22 | ReLU | 1x1x4096 |
| 23 | Dropout | 1x1x1000 |
| 24 | FC | 1x1x1000 |
| 25 | Softmax | 1x1x1000 |

```python
model = Sequential()

model.add(Conv2D(96, (7, 7), strides=(2, 2), input_shape=(224, 224, 3), activation='relu'))

model.add(MaxPooling2D((3, 3), strides=(2, 2)))

model.add(Conv2D(256, (5, 5), activation='relu'))

model.add(MaxPooling2D((3, 3), strides=(2, 2)))

model.add(Conv2D(384, (3, 3), activation='relu'))

model.add(Conv2D(384, (3, 3), activation='relu'))

model.add(Conv2D(256, (3, 3), activation='relu'))

model.add(MaxPooling2D((3, 3), strides=(2, 2))

model.add(Flatten())
model.add(Dense(4096, activation='relu'))
model.add(Dropout(0.5))
model.add(Dense(4096, activation='relu'))
model.add(Dropout(0.5))
model.add(Dense(1000, activation='softmax'))
```

