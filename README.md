# Histogram-Equalization
Nama : Nadhif Fathur Rahman      
Kelas : TIF22A      
NIM : 23422027

**Soal :**
- Buat program dari algoritma berikut, untuk Histogram Equalization

  # Jawaban

  ```python
  import cv2
import numpy as np
import matplotlib.pyplot as plt

# Memuat gambar dan mengubahnya ke skala abu-abu
gambar = cv2.imread('path/to/image.jpg', cv2.IMREAD_GRAYSCALE)  # Ganti 'path/to/image.jpg' dengan lokasi gambar Anda
tinggi, lebar = gambar.shape

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
