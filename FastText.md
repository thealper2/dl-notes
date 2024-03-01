FastText, Facebook tarafından geliştirilmiştir. Karakter n-gramlarını dikkate alarak kelime temsilleri oluşturur. Bu, kelime seviyesindeki gömme yöntemlerine kıyasla küçük veri setlerinde daha iyi performans göstermesini sağlar. 

```python
import fasttext

# Örnek metin veri seti
train_data = "train.txt"
test_data = "test.txt"

# Modeli eğitme
model = fasttext.train_supervised(input=train_data, lr=0.1, epoch=25, wordNgrams=2)

# Modeli değerlendirme
result = model.test(test_data)
print("Precision:", result[1])
print("Recall:", result[2])
print("F1 Score:", result[3])

# Örnek metin sınıflandırma
text = "Bu bir örnek metin."
predicted_label = model.predict(text)
print("Predicted Label:", predicted_label[0][0])
```