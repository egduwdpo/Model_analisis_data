Deskripsi Program

Program ini dibuat untuk mempelajari berbagai konsep analisis data menggunakan Python, yaitu:

RMSE (Root Mean Square Error)
Standard Deviation
Korelasi
Regresi Linear
Regresi Polinomial
Regresi Multi Variabel
Visualisasi Data menggunakan Matplotlib

Library yang digunakan:

NumPy → operasi numerik
Pandas → pengolahan data
Matplotlib → visualisasi grafik
Scikit-Learn → machine learning & evaluasi model
1. IMPORT LIBRARY
import numpy as np
import pandas as pd
from sklearn.metrics import mean_squared_error
import matplotlib.pyplot as plt
Penjelasan
import numpy as np

Mengimpor library NumPy dan memberi alias np.

NumPy digunakan untuk:

operasi matematika
array numerik
statistik
perhitungan cepat
import pandas as pd

Mengimpor Pandas dengan alias pd.

Digunakan untuk:

membuat tabel data
manipulasi dataset
analisis data
from sklearn.metrics import mean_squared_error

Mengambil fungsi mean_squared_error dari Scikit-Learn.

Digunakan untuk menghitung:

MSE
RMSE
import matplotlib.pyplot as plt

Mengimpor modul visualisasi Matplotlib.

Digunakan untuk:

membuat grafik
plot
chart
visualisasi statistik
2. CONTOH RMSE
data_aktual = [100, 120, 130, 140, 150]
data_prediksi = [98, 125, 128, 145, 148]
Penjelasan

Membuat dua data:

Data	Fungsi
data_aktual	nilai sebenarnya
data_prediksi	hasil prediksi model
Menghitung Error
error = data_aktual[i] - data_prediksi[i]
Logika

Menghitung selisih:

Error=Aktual−Prediksi

Jika:

positif → prediksi terlalu kecil
negatif → prediksi terlalu besar
Menyimpan Error
errors.append(error)

Menambahkan error ke dalam list.

3. MENGHITUNG RMSE MANUAL
squared_errors = [e**2 for e in errors]
Penjelasan

Mengkuadratkan semua error.

Contoh:

(−5)
2
=25

Tujuannya:

menghilangkan nilai negatif
memperbesar error besar
mean_squared_error_manual = sum(squared_errors) / len(squared_errors)

Menghitung rata-rata error kuadrat.

Rumus:

MSE=
n
∑error
2
	​

rmse_manual = mean_squared_error_manual ** 0.5

Akar kuadrat dari MSE.

Rumus:

RMSE=
MSE
	​

4. RMSE DENGAN NUMPY
rmse_numpy = np.sqrt(np.mean((np.array(data_aktual) - np.array(data_prediksi))**2))
Penjelasan per bagian
np.array()

Mengubah list menjadi array NumPy.

data_aktual - data_prediksi

Menghitung semua error sekaligus.

**2

Mengkuadratkan error.

np.mean()

Menghitung rata-rata.

np.sqrt()

Menghitung akar kuadrat.

5. RMSE DENGAN SKLEARN
rmse_sklearn = np.sqrt(mean_squared_error(data_aktual, data_prediksi))
Logika
mean_squared_error() menghitung MSE
np.sqrt() mengubah menjadi RMSE
6. STANDARD DEVIATION
mean = sum(nilai_siswa) / len(nilai_siswa)
Penjelasan

Menghitung rata-rata data.

Rumus:

x
ˉ
=
n
∑x
	​

Variance
variance = sum((x - mean)**2 for x in nilai_siswa) / len(nilai_siswa)
Logika

Mengukur penyebaran data dari rata-rata.

Langkah:

cari selisih data dengan mean
kuadratkan
jumlahkan
bagi jumlah data
Standard Deviation
std_dev_population = variance ** 0.5

Rumus:

SD=
Variance
	​


Semakin besar SD:

data semakin menyebar

Semakin kecil SD:

data semakin konsisten
7. MEMBUAT DATAFRAME PANDAS
df = pd.DataFrame(data)
Penjelasan

Mengubah dictionary menjadi tabel.

Contoh:

Bulan	Penjualan
1	120
2	135
8. MENAMBAH KOLOM ERROR
df['Error'] = df['Penjualan_Aktual'] - df['Penjualan_Prediksi']
Logika

Membuat kolom baru bernama Error.

9. MENAMBAH SQUARED ERROR
df['Squared_Error'] = df['Error'] ** 2

Menyimpan error kuadrat.

10. MAE (MEAN ABSOLUTE ERROR)
mae = df['Error'].abs().mean()
Penjelasan
.abs()

Mengubah error menjadi positif.

.mean()

Menghitung rata-rata.

Rumus:

MAE=
n
∑∣error∣
	​

11. VISUALISASI MATPLOTLIB
Membuat Figure
plt.figure(figsize=(12, 5))

Membuat area grafik ukuran:

lebar = 12
tinggi = 5
Membuat Subplot
plt.subplot(1, 2, 1)

Artinya:

1 baris
2 kolom
grafik ke-1
12. LINE PLOT
plt.plot(df['Bulan'], df['Penjualan_Aktual'])
Penjelasan

Membuat grafik garis.

Parameter:

sumbu X → bulan
sumbu Y → penjualan
13. BAR CHART ERROR
plt.bar(df['Bulan'], df['Error'])

Membuat diagram batang error.

14. MENYIMPAN GAMBAR
plt.savefig('analisis_rmse_sd.png')

Menyimpan grafik ke file PNG.

15. FUNCTION PYTHON
def hitung_metrik(actual, predicted):
Penjelasan

Membuat fungsi reusable.

Keuntungan:

kode lebih rapi
dapat dipanggil berkali-kali
mudah maintenance
16. MAPE
mape = np.mean(np.abs(errors / actual)) * 100
Rumus
MAPE=
n
1
	​

∑
	​

actual
error
	​

	​

×100

Digunakan untuk:

mengukur error dalam persen
17. R-SQUARED
r_squared = 1 - (ss_res / ss_tot)
Penjelasan
ss_res

Jumlah error model.

ss_tot

Total variasi data.

Rumus
R
2
=1−
SS
tot
	​

SS
res
	​

	​


Interpretasi:

mendekati 1 → model bagus
mendekati 0 → model buruk
18. KORELASI PEARSON
korelasi_numpy = np.corrcoef(x, y)[0, 1]
Fungsi

Mengukur hubungan antar variabel.

Nilai:

+1 → sangat positif
0 → tidak ada hubungan
-1 → sangat negatif
19. INTERPRETASI KORELASI
if r_abs >= 0.80:

Digunakan untuk menentukan:

sangat kuat
kuat
sedang
lemah
20. MATRIX KORELASI
matriks_korelasi = df[kolom_analisis].corr()
Penjelasan

Menghitung hubungan semua kolom numerik.

21. KORELASI SPEARMAN
corr(method='spearman')

Digunakan jika:

data tidak normal
data ranking
22. SCATTER PLOT
axes[0].scatter(x, y)

Menampilkan hubungan antar titik data.

23. GARIS REGRESI
m, b = np.polyfit(x, y, 1)
Penjelasan
m

Slope / kemiringan.

b

Intercept.

Persamaan:

y=mx+b
24. REGRESI LINEAR
model_linear = LinearRegression()

Membuat model regresi linear.

Training Model
model_linear.fit(x, y)

Melatih model menggunakan data.

Prediksi
model_linear.predict(x)

Menghasilkan prediksi.

25. REGRESI POLINOMIAL
PolynomialFeatures(derajat)

Mengubah:

linear
menjadi:
kuadrat
kubik
polynomial
Contoh Derajat 2
y=ax
2
+bx+c
26. REGRESI MULTI VARIABEL
X_multi = df[['Biaya_Iklan', 'Jumlah_Pembeli']]

Menggunakan lebih dari satu variabel input.

Persamaan
Y=aX
1
	​

+bX
2
	​

+c
27. VISUALISASI SEMUA MODEL
fig, axes = plt.subplots(2, 2)

Membuat:

2 baris
2 kolom
total 4 grafik
28. RINGKASAN MODEL
ringkasan = pd.DataFrame({...})

Membuat tabel perbandingan model.

29. MENENTUKAN MODEL TERBAIK
model_terbaik = ringkasan.loc[ringkasan['R²'].idxmax(), 'Model']
Logika
mencari R² tertinggi
memilih model terbaik
30. KESIMPULAN PROGRAM

Program ini mempelajari:

Materi	Fungsi
RMSE	Mengukur error prediksi
Standard Deviation	Mengukur penyebaran data
Korelasi	Mengukur hubungan data
Regresi Linear	Prediksi linear
Regresi Polynomial	Prediksi non-linear
Multi Variabel	Prediksi banyak faktor
Visualisasi	Menampilkan data secara grafis
Output yang Dihasilkan

Program menghasilkan:

Tabel analisis
Nilai statistik
Nilai korelasi
Nilai regresi
Grafik PNG:
analisis_rmse_sd.png
analisis_korelasi.png
kurva_regresi.png
Cara Menjalankan
Install Library
pip install numpy pandas matplotlib scikit-learn
Jalankan Program
python nama_file.py
Struktur Konsep Utama
Data
 ↓
Error
 ↓
RMSE / MAE / MAPE
 ↓
Korelasi
 ↓
Regresi
 ↓
Visualisasi
 ↓
Evaluasi Model
