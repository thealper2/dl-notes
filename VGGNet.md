2014'de ImageNet ILSVRC (Büyük Ölçekli Görsel Tanıma Yarışması)'de sunuldu. Yarışmayı, GoogleLeNet modelinden sonra tamamlayarak ikinci oldu. VGG Group (Oxford) tarafından sunulmuştur. Ağın derinliğinin önemi üzerinde durulmuştur. Farklı sürümleri de bulunur.  AlexNet mimarisinde kullanılan yüksek kernel boyutları azaltılmıştır. Sadece 3x3  filtre ve 2x2 lik havuz  boyutları kullanılarak ağa basit kazandırılmış ve derinlik korunmuştur. 

| Katman | Layer | Size | Filter | Kernel Size | Stride | Padding | Activation |
| - | - | - | - | - | - | - | - |
| 0 | Input | 224x224x3 |
| 1-2 | Convolution | 224x224x64 | 3x3 | 64 | 1 | 0 | relu |
| 3 | Max Pooling | 112x112x64 | 3x3 | - | 2 | 0 | relu |
| 4-5 | Convolution | 112x112x128 | 3x3 | 128 | 1 | 0 | relu |
| 6 | Max Pooling | 56x56x128 | 2x2 | - | 2 | 0 | relu |
| 7-8 | Convolution | 56x56x256 | 3x3 | 256 | 1 | 0 | relu |
| 9 | Max Pooling | 28x28x256 | 2x2 | - | 2 | 0 | relu |
| 10-11-12 | Convolution | 28x28x512 | 3x3 | 512 | 1 | 0 | relu |
| 13 | Max Pooling | 14x14x512 | 2x2 | - | 2 | 0 | relu |
| 14-15-16 | Convolution | 14x14x512 | 3x3 | 512 | 1 | 0 | relu |
| 17 | Max Pooling | 7x7x512 | 2x2 | - | 2 | 0 | relu |
| 18 | FC | 
| 19 | FC | 
| 20 | FC | 
| 21 | Softmax |

```python
# VGG-16
model = Sequential([
	Conv2D(filters=64, kernel_size=(3,3), padding="same", activation="relu"),
	Conv2D(filters=64, kernel_size=(3,3), padding="same", activation="relu"),
	MaxPooling2D((2, 2)),
	
	Conv2D(filters=128, kernel_size=(3,3), padding="same", activation="relu"),
	Conv2D(filters=128, kernel_size=(3,3), padding="same", activation="relu"),
	MaxPooling2D((2, 2)),
	
	Conv2D(filters=256, kernel_size=(3,3), padding="same", activation="relu"),
	Conv2D(filters=256, kernel_size=(3,3), padding="same", activation="relu"),
	Conv2D(filters=256, kernel_size=(3,3), padding="same", activation="relu"),
	MaxPooling2D((2, 2)),
	
	Conv2D(filters=512, kernel_size=(3,3), padding="same", activation="relu"),
	Conv2D(filters=512, kernel_size=(3,3), padding="same", activation="relu"),
	Conv2D(filters=512, kernel_size=(3,3), padding="same", activation="relu"),
	MaxPooling2D((2, 2)),
	
	Conv2D(filters=512, kernel_size=(3,3), padding="same", activation="relu"),
	Conv2D(filters=512, kernel_size=(3,3), padding="same", activation="relu"),
	Conv2D(filters=512, kernel_size=(3,3), padding="same", activation="relu"),
	MaxPooling2D((2, 2)),
	
	Flatten(),
	Dense(4096, activation="relu"),
	Dense(4096, activation="relu"),
	Dense(1000, activation="softmax")					
])
```

