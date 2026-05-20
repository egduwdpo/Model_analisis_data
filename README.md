# README.md

# Analisis Statistik dan Regresi Menggunakan Python

## Deskripsi Program

Program ini dibuat untuk mempelajari berbagai konsep analisis data menggunakan Python, yaitu:

* RMSE (Root Mean Square Error)
* Standard Deviation
* Korelasi
* Regresi Linear
* Regresi Polinomial
* Regresi Multi Variabel
* Visualisasi Data menggunakan Matplotlib

---

# Library yang Digunakan

```python
import numpy as np
import pandas as pd
from sklearn.metrics import mean_squared_error
import matplotlib.pyplot as plt
```

## Penjelasan

| Library      | Fungsi                               |
| ------------ | ------------------------------------ |
| NumPy        | Operasi matematika dan array numerik |
| Pandas       | Pengolahan dan analisis data         |
| Matplotlib   | Visualisasi grafik                   |
| Scikit-Learn | Machine Learning dan evaluasi model  |

---

# 1. Menghitung RMSE

## Data Aktual dan Prediksi

```python
data_aktual = [100, 120, 130, 140, 150]
data_prediksi = [98, 125, 128, 145, 148]
```

### Penjelasan

* `data_aktual` → data sebenarnya
* `data_prediksi` → hasil prediksi model

---

## Menghitung Error

```python
error = data_aktual[i] - data_prediksi[i]
```

### Rumus

[
Error = Aktual - Prediksi
]

### Logika

* Positif → prediksi terlalu kecil
* Negatif → prediksi terlalu besar

---

## Menghitung RMSE Manual

```python
squared_errors = [e**2 for e in errors]
mean_squared_error_manual = sum(squared_errors) / len(squared_errors)
rmse_manual = mean_squared_error_manual ** 0.5
```

### Penjelasan

1. Error dikuadratkan
2. Dijumlahkan
3. Dibagi jumlah data
4. Diakar kuadratkan

### Rumus RMSE

[
RMSE = \sqrt{\frac{\sum error^2}{n}}
]

---

## RMSE Menggunakan NumPy

```python
rmse_numpy = np.sqrt(np.mean((np.array(data_aktual) - np.array(data_prediksi))**2))
```

### Penjelasan

* `np.array()` → ubah list menjadi array
* `-` → hitung error
* `**2` → kuadrat error
* `np.mean()` → rata-rata
* `np.sqrt()` → akar kuadrat

---

## RMSE Menggunakan Scikit-Learn

```python
rmse_sklearn = np.sqrt(mean_squared_error(data_aktual, data_prediksi))
```

### Penjelasan

* `mean_squared_error()` → hitung MSE
* `np.sqrt()` → ubah menjadi RMSE

---

# 2. Standard Deviation

## Menghitung Mean

```python
mean = sum(nilai_siswa) / len(nilai_siswa)
```

### Rumus

[
\bar{x} = \frac{\sum x}{n}
]

---

## Menghitung Variance

```python
variance = sum((x - mean)**2 for x in nilai_siswa) / len(nilai_siswa)
```

### Penjelasan

Variance mengukur penyebaran data terhadap rata-rata.

---

## Menghitung Standard Deviation

```python
std_dev_population = variance ** 0.5
```

### Rumus

[
SD = \sqrt{Variance}
]

### Interpretasi

* SD besar → data menyebar
* SD kecil → data konsisten

---

# 3. DataFrame Pandas

## Membuat DataFrame

```python
df = pd.DataFrame(data)
```

### Penjelasan

Mengubah dictionary menjadi tabel.

---

## Menambahkan Kolom Error

```python
df['Error'] = df['Penjualan_Aktual'] - df['Penjualan_Prediksi']
```

### Penjelasan

Membuat kolom error baru.

---

## Menambahkan Squared Error

```python
df['Squared_Error'] = df['Error'] ** 2
```

### Penjelasan

Menyimpan error kuadrat.

---

# 4. Mean Absolute Error (MAE)

```python
mae = df['Error'].abs().mean()
```

### Rumus

[
MAE = \frac{\sum |error|}{n}
]

### Penjelasan

* `.abs()` → ubah menjadi positif
* `.mean()` → rata-rata

---

# 5. Visualisasi Data

## Membuat Figure

```python
plt.figure(figsize=(12, 5))
```

### Penjelasan

Membuat area grafik ukuran:

* lebar = 12
* tinggi = 5

---

## Membuat Subplot

```python
plt.subplot(1, 2, 1)
```

### Penjelasan

* 1 baris
* 2 kolom
* grafik ke-1

---

## Membuat Line Plot

```python
plt.plot(df['Bulan'], df['Penjualan_Aktual'])
```

### Fungsi

Membuat grafik garis.

---

## Membuat Bar Chart

```python
plt.bar(df['Bulan'], df['Error'])
```

### Fungsi

Membuat diagram batang error.

---

## Menyimpan Grafik

```python
plt.savefig('analisis_rmse_sd.png')
```

### Fungsi

Menyimpan grafik menjadi file PNG.

---

# 6. Function Python

## Membuat Fungsi

```python
def hitung_metrik(actual, predicted):
```

### Fungsi

Membuat kode reusable agar:

* lebih rapi
* mudah digunakan ulang
* mudah maintenance

---

# 7. MAPE (Mean Absolute Percentage Error)

```python
mape = np.mean(np.abs(errors / actual)) * 100
```

### Rumus

[
MAPE = \frac{1}{n}\sum \left|\frac{error}{actual}\right| \times 100
]

### Fungsi

Mengukur error dalam bentuk persen.

---

# 8. R-Squared

```python
r_squared = 1 - (ss_res / ss_tot)
```

### Rumus

[
R^2 = 1 - \frac{SS_{res}}{SS_{tot}}
]

### Interpretasi

* mendekati 1 → model bagus
* mendekati 0 → model buruk

---

# 9. Korelasi Pearson

```python
korelasi_numpy = np.corrcoef(x, y)[0, 1]
```

### Fungsi

Mengukur hubungan antar variabel.

### Nilai Korelasi

| Nilai | Arti               |
| ----- | ------------------ |
| 1     | Positif sempurna   |
| 0     | Tidak ada hubungan |
| -1    | Negatif sempurna   |

---

# 10. Korelasi Spearman

```python
corr(method='spearman')
```

### Fungsi

Digunakan untuk:

* data tidak normal
* data ranking

---

# 11. Scatter Plot

```python
axes[0].scatter(x, y)
```

### Fungsi

Menampilkan hubungan antar titik data.

---

# 12. Regresi Linear

## Membuat Model

```python
model_linear = LinearRegression()
```

---

## Training Model

```python
model_linear.fit(x, y)
```

### Fungsi

Melatih model menggunakan data.

---

## Prediksi

```python
model_linear.predict(x)
```

### Fungsi

Menghasilkan prediksi.

---

## Persamaan Regresi Linear

[
y = mx + b
]

Keterangan:

* `m` = slope
* `b` = intercept

---

# 13. Regresi Polinomial

```python
PolynomialFeatures(derajat)
```

### Fungsi

Mengubah model linear menjadi:

* kuadrat
* kubik
* polynomial

---

## Contoh Persamaan Derajat 2

[
y = ax^2 + bx + c
]

---

# 14. Regresi Multi Variabel

```python
X_multi = df[['Biaya_Iklan', 'Jumlah_Pembeli']]
```

### Fungsi

Menggunakan lebih dari satu variabel input.

---

## Persamaan

[
Y = aX_1 + bX_2 + c
]

---

# 15. Visualisasi Semua Model

```python
fig, axes = plt.subplots(2, 2)
```

### Fungsi

Membuat:

* 2 baris
* 2 kolom
* total 4 grafik

---

# 16. Ringkasan Model

```python
ringkasan = pd.DataFrame({...})
```

### Fungsi

Membuat tabel perbandingan model.

---

# 17. Menentukan Model Terbaik

```python
model_terbaik = ringkasan.loc[ringkasan['R²'].idxmax(), 'Model']
```

### Logika

* mencari nilai R² tertinggi
* menentukan model terbaik

---

# Output Program

Program menghasilkan:

* Tabel analisis
* Nilai statistik
* Nilai korelasi
* Grafik PNG:

  * `analisis_rmse_sd.png`
  * `analisis_korelasi.png`
  * `kurva_regresi.png`

---

# Cara Menjalankan Program

## Install Dependency

```bash
pip install numpy pandas matplotlib scikit-learn
```

---

## Menjalankan Program

```bash
python nama_file.py
```

---

# Struktur Analisis Program

```text
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
```

---

# Kesimpulan

Program ini mempelajari konsep:

* evaluasi model prediksi
* statistik dasar
* analisis hubungan data
* machine learning sederhana
* visualisasi data

Cocok digunakan untuk:

* pembelajaran data science dasar
* tugas kuliah statistik
* analisis penjualan
* penelitian sederhana
