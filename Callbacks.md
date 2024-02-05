- Model Checkpoint: eğitim sırasında modelin belirli aralıklarla kaydedilmesini sağlar.

| Parametre | Açıklama |
| ---- | ---- |
| filepath | Kaydedilecek dosyanın yolu. |
| monitor | İzlenecek metriğin adı. |
| verbose | Çıktı durumu. |
| save_best_only | Sadece en iyi performans gösterdiği durumları kaydet. |
| mode | Monitor metriğinin neye göre değerlendirileceği. "max" veya "min". |
| period | Kaydetme aralığı. |
```python
from keras.callbacks import ModelCheckpoint

checkpoint = ModelCheckpoint(filepath='best_model.h5',
							monitor='val_accuracy',
							verbose=1,
							save_best_only=True,
							mode='max')
```

- BackupAndRestore: Eğitim sırasında modelin yedeklerini alarak ve geri yükleyerek eğitim sırasında oluşabilecek herhangi bir kesintiden sonra eğitimin devam etmesini sağlar.

| Parametre | Açıklama |
| ---- | ---- |
| backup_dir | Yedekleme dizini. |
| frequency | Yedekleme sıklığı. |
```python
from keras.callbacks import BackupAndRestore

backup = BackupAndRestore(backup_dir,
						 save_freq="epoch")
```

- TensorBoard: Tensorflow'un görselleştirme aracıdır ve modelin performansını izlemek, hata analizi yapmak ve eğitim sürecini anlamak için kullanılır.

| Parametre | Açıklama |
| ---- | ---- |
| log_dir | Log kaydedileceği dizin. |
| histogram_freq | Histogram güncelleme sıklığı. |
| write_graph | Model grafiğinin tensorboard'da gösterilmesi |
| write_images | Modelin görsel tanımının tensorboard'da gösterilmesi. |
```python
from keras.callbacks import Tensorboard

tensorboard_callback = TensorBoard(log_dir='./logs')
```

- EarlyStopping: Belirli bir metriği izleyerek iyileşmediği durumlarda eğitimi durdurur. Bu, overfitting durumlarında eğitimi sonlandırmak için kullanılır.

| Parametre | Açıklama |
| ---- | ---- |
| monitor | Takip edilen metrik. |
| patience | İzlenecek epoch sayısı. |
| mode | Değerlendirme türü "min" veya "max". |
| baseline | Eğitimin durdurulması için belirli bir referans değeri. |
| restore_best_weights | En iyi modelin ağırlıklarını geri yükleme. |
```python
from keras.callbacks import EarlyStopping

early_stopping = EarlyStopping(monitor='val_loss', patience=5)
```

- LearningRateScheduler: Eğitim sırasında öğrenme oranını değiştirmek için kullanılır. 

```python
from keras.callbacks import LearningRateScheduler

def lr_schedule(epoch, lr): 
	if epoch < 10:
		return lr
	else:
		return lr * np.exp(-0.5)

lr_scheduler = LearningRateScheduler(schedule=lr_scheduler)
```

- ReduceLROnPlateau: Eğitim sırasında belirli bir metriği iyileşmediği durumlarda öğrenme oranını düşürmek için kullanılır. 

| Parametre | Açıklama |
| ---- | ---- |
| monitor | Takip edilecek metrik adı. |
| factor | Öğrenme oranını azaltmak için çarpan. |
| patience | İzlenecek epoch sayısı. |
| mode | Değerlendirme türü. |
| cooldown | Öğrenme oranını azalttıktan sonra bekleyeceği epoch sayısı. |
```python
from keras.callbacks import ReduceLROnPlateau

lr_plat = ReduceLROnPlateua(monitor='val_loss', patience=3, factor=0.2)
```

- CSVLogger: Eğitim sırasında modelin metriklerini bir CSV dosyasına kaydeder.

```python
from keras.callbacks import CSVLogger

csv_log = CSVLogger(filename='file.csv', seperator=',')
```

