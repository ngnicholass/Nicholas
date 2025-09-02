1. Ringkasan Cara Kerja Metode IQR

Metode Interquartile Range (IQR) digunakan untuk mendeteksi dan menghapus outlier.
Prinsipnya:

1. Hitung Q1 (kuartil bawah, persentil 25) dan Q3 (kuartil atas, persentil 75).
2. Hitung IQR = Q3 – Q1.
3. Tentukan batas bawah = Q1 – 1.5 × IQR dan batas atas = Q3 + 1.5 × IQR.
4. Data yang berada di luar batas bawah atau atas dianggap outlier.
5. Outlier dapat dihapus atau ditandai.

Intinya: kita buang data yang terlalu kecil atau terlalu besar dibanding distribusi normal.

2. Eksperimen dengan Data Minat Baca Indonesia

1. Load Data
import pandas as pd

# Baca CSV
df = pd.read_csv("/content/TGM 2020-2023_eng.csv")

# Lihat struktur data
print(df.head())
print(df.info())

2. Visualisasi Histogram (Sebelum Outlier Removal)
import matplotlib.pyplot as plt

plt.hist(df["Reading_Interest"], bins=20, edgecolor="black")
plt.title("Histogram Sebelum Menghapus Outlier")
plt.xlabel("Reading Interest")
plt.ylabel("Frekuensi")
plt.show()

3. Fungsi Menghapus Outlier dengan IQR
import numpy as np

def remove_outliers_iqr(data, column):
    Q1 = data[column].quantile(0.25)
    Q3 = data[column].quantile(0.75)
    IQR = Q3 - Q1
    lower = Q1 - 1.5 * IQR
    upper = Q3 + 1.5 * IQR
    return data[(data[column] >= lower) & (data[column] <= upper)]

4. Terapkan ke Kolom Reading Interest
df_no_outlier = remove_outliers_iqr(df, "Reading_Interest")

print("Jumlah data sebelum:", len(df))
print("Jumlah data sesudah:", len(df_no_outlier))

5. Histogram Sesudah Outlier Removal
plt.hist(df_no_outlier["Reading_Interest"], bins=20, edgecolor="black")
plt.title("Histogram Sesudah Menghapus Outlier")
plt.xlabel("Reading Interest")
plt.ylabel("Frekuensi")
plt.show()

6. Opsional: Hapus Outlier di Semua Kolom Numerik
df_clean = df.copy()
for col in df_clean.select_dtypes(include=np.number).columns:
    df_clean = remove_outliers_iqr(df_clean, col)

print("Jumlah data final:", len(df_clean))
