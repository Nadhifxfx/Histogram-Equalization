# Histogram-Equalization
Nama : Nadhif Fathur Rahman      
Kelas : TIF22A      
NIM : 23422027

**Soal :**
- Buat program dari algoritma berikut, untuk Histogram Equalization
```
'Histogram Egualization
Foriz0 To Picture1.ScaleWidth - 1
For j - 0 To Picture 1.ScaleHeight - 1
  w = Picture 1.Point(i, j)
  r = w And RGB(255, 0, 0)
  g = Int((w And RGB(O, 255, 0)) / 256)
  b = Int(Int((w And RGB(O, 0, 255)) / 256) / 256)
  xg = int((r + g +b)/ 3)
  yg 7 Int(256 * c(xg) / 128 / 128)
  h2(yg) - h2(yg) + 1
  Picture2.PSet (i, j), RGB(yg, ya, ya)
Next j
Next |
For i = 0 To 255
  MSChart1.Row = i + 1
  MSChart1.Data = hi(i)
  MSChart1.RowLabel = Trim(Str(i))     
  MSChart2.Row-i + 1
  MSChart2.Data = h2(i)
  MSChart2.RowLabel = Trim(Str(i))
Next i 
```
  # Jawaban

```python
import cv2
import numpy as np
import matplotlib.pyplot as plt

# Memuat gambar dan mengubahnya ke skala abu-abu
gambar = cv2.imread('path/to/image.jpg', cv2.IMREAD_GRAYSCALE) 

# Inisialisasi histogram untuk intensitas sebelum dan sesudah equalization
h = np.zeros(256)
h2 = np.zeros(256)

# Hitung histogram dari gambar asli
for i in range(lebar):
    for j in range(tinggi):
        h[gambar[j, i]] += 1

# Hitung CDF (Cumulative Distribution Function) untuk histogram equalization
cdf = h.cumsum()
cdf_normalized = (cdf - cdf.min()) * 255 / (cdf.max() - cdf.min())
cdf_normalized = cdf_normalized.astype('uint8')

# Terapkan histogram equalization menggunakan CDF
gambar_equalized = cdf_normalized[gambar]

# Hitung histogram dari gambar setelah equalization
for i in range(lebar):
    for j in range(tinggi):
        h2[gambar_equalized[j, i]] += 1

# Tampilkan hasil
plt.figure(figsize=(12, 6))

# Tampilkan gambar asli
plt.subplot(2, 2, 1)
plt.imshow(gambar, cmap='gray')
plt.title("Gambar Asli")
plt.axis("off")

# Tampilkan histogram gambar asli
plt.subplot(2, 2, 2)
plt.plot(h, color='black')
plt.title("Histogram Gambar Asli")

# Tampilkan gambar setelah equalization
plt.subplot(2, 2, 3)
plt.imshow(gambar_equalized, cmap='gray')
plt.title("Gambar Setelah Histogram Equalization")
plt.axis("off")

# Tampilkan histogram gambar setelah equalization
plt.subplot(2, 2, 4)
plt.plot(h2, color='black')
plt.title("Histogram Setelah Equalization")

plt.tight_layout()
plt.show()
```

**Hasil Gambar**

![alt text](https://github.com/Nadhifxfx/Histogram-Equalization/blob/main/assets/Hasil%20gambar%20Histogram%20Equalization.png?raw=true)
