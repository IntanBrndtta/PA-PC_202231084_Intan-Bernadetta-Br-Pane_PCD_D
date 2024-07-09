
# UAS Praktikum PCD
## Geometrix Citra
Geometrix citra merujuk pada teknik atau proses pemrosesan gambar untuk mengubah atau memanipulasi geometri dari sebuah citra. Ini bisa mencakup rotasi, perubahan skala (resize), pemangkasan (cropping), pemutaran (flipping), atau translasi. Teknik ini sering digunakan dalam pengolahan gambar untuk berbagai aplikasi seperti komputer grafis, pengolahan citra medis, dan analisis visual.

## Kelebihan Dan Kekurangan
Kelebihan:
1. Rotasi:
Kelebihan: Berguna untuk orientasi gambar yang benar, penting dalam aplikasi seperti pengenalan objek.

Kekurangan: Mungkin menyebabkan hilangnya detail jika interpolasi tidak dilakukan dengan baik.

2. Perubahan Skala (Resize):
Kelebihan: Memungkinkan penyesuaian ukuran gambar untuk berbagai kebutuhan, seperti tampilan web atau cetak.

Kekurangan: Dapat menyebabkan distorsi atau kehilangan detail pada ukuran yang lebih kecil.

3. Pemangkasan (Cropping):
Kelebihan: Membantu fokus pada area penting dari gambar, menghilangkan bagian yang tidak diinginkan.

Kekurangan: Bisa menghilangkan konteks penting dari gambar.

4. Pemutaran (Flipping):
Kelebihan: Berguna dalam augmentasi data untuk pelatihan model pembelajaran mesin, memperbaiki orientasi citra.

Kekurangan: Dapat membingungkan jika arah gambar memiliki arti penting (misalnya, teks).

5. Translasi:
Kelebihan: Menggeser posisi objek dalam gambar tanpa mengubah bentuk atau ukuran, berguna untuk pemosisian ulang.

Kekurangan: Bisa menyebabkan bagian dari gambar keluar dari batas frame, kehilangan informasi.

### Adapun Implementasinya
### Import Library
import cv2 (untuk menjalakan fungsi library open cv)

import numpy as np (untuk menjalakan fungsi array)

import matplotlib.pyplot as plt (menampilkan fungsi visualisasi data)

img = cv2.imread('intan2.jpg') #Membuat variabel img untuk mengimport atau membaca file

img = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

#### Rotasi gambar 90 derajat
rows, cols, _ = img.shape

M = cv2.getRotationMatrix2D((cols / 2, rows / 2), 45, 1)
rotated_image = cv2.warpAffine(img, M, (cols, rows))

#### Resize gambar menjadi setengah ukuran
resized_image = cv2.resize(img, (cols // 8, rows // 8))

#### Crop gambar menjadi bagian tengah
crop_size = 500  # Ukuran sisi kotak yang akan di-crop

start_y = rows // 2 - crop_size // 2

start_x = cols // 2 - crop_size // 2

cropped_image = img[start_y:start_y + crop_size, start_x:start_x + crop_size]

#### Flip gambar secara horizontal
flipped_image = cv2.flip(img, 1)

#### Translate gambar
M_translate = np.float32([[1, 0, 50], [0, 1, 20]])  (Matriks transformasi untuk translasi)

translated_image = cv2.warpAffine(img, M_translate, (cols, rows))

#### Menampilkan gambar-gambar
plt.figure(figsize=(10, 10))

#### Gambar asli
plt.subplot(2, 3, 1)

plt.imshow(img)

plt.title('Citra Asli')

plt.axis('on')

#### Gambar yang sudah dirotasi
plt.subplot(2, 3, 2)

plt.imshow(rotated_image)

plt.title('After Rotated')

plt.axis('on')

#### Gambar yang sudah diresize
plt.subplot(2, 3, 3)

plt.imshow(resized_image)

plt.title('After Resized')

plt.axis('on')

#### Gambar yang sudah di-crop
plt.subplot(2, 3, 4)

plt.imshow(cropped_image)

plt.title('After Cropped')

plt.axis('on')

#### Gambar yang sudah diflip
plt.subplot(2, 3, 5)

plt.imshow(flipped_image)

plt.title('After Flipped')

plt.axis('on')

#### Gambar yang sudah diterjemahkan (translated)
plt.subplot(2, 3, 6)

plt.imshow(translated_image)

plt.title('After Translated')

plt.axis('on')

plt.tight_layout()

plt.show()






