# Optimized-KMeans-with-GradientDescent

### **Clustering Aktivitas Industri Menggunakan K-Means yang Dioptimalkan dengan Gradient Descent (Steepest Descent)**

Proyek ini mengimplementasikan algoritma **K-Means Clustering from scratch** menggunakan pendekatan **Steepest Descent** untuk meminimalkan *Within-Cluster Sum of Squares (WCSS)*.
Tidak ada fungsi bawaan `sklearn.KMeans` yang digunakan — seluruh proses optimasi, perhitungan gradien, dan update centroid ditulis secara manual untuk mendemonstrasikan konsep dasar **Metode Optimasi Non-Linear**.

---

## ✨ **Highlight Proyek**

* ✔ Implementasi **Gradient Descent** untuk meminimalkan WCSS
* ✔ K-Means dibangun **sepenuhnya dari nol**
* ✔ Menggunakan **adaptive learning rate** untuk mencegah divergensi
* ✔ Studi kasus nyata pada dataset aktivitas operasional (multidimensi)
* ✔ Feature engineering lengkap: durasi, siklis waktu, one-hot encoding, Yeo-Johnson transform
* ✔ Visualisasi: Loss curve, PCA 2D, bar plot cluster, radar plot
* ✔ Analisis karakteristik tiap cluster secara menyeluruh

---

## 📌 **1. Latar Belakang**

Dataset berisi data aktivitas harian yang mencakup informasi seperti:

* Jarak tempuh
* Durasi dan waktu bergerak
* Kecepatan rata-rata
* Detak jantung
* Jenis aktivitas

Tujuan utama adalah **mengidentifikasi pola aktivitas** dan mengelompokkan data ke dalam klaster yang bermakna menggunakan pendekatan optimasi.

---

## 📐 **2. Rumusan Masalah Optimasi**

K-Means bertujuan **meminimalkan WCSS**:

[
J(\mu)=\sum_{j=1}^k \sum_{x_i \in C_j} \Vert x_i - \mu_j \Vert^2
]

Untuk meminimalkan fungsi ini, dilakukan pendekatan **Gradient Descent** melalui perhitungan gradien:

[
\nabla_{\mu_j} J = 2\left( N_j \mu_j - \sum_{x_i \in C_j} x_i \right)
]

Update rule:

[
\mu_j^{(t+1)} = \mu_j^{(t)} - \alpha \nabla_{\mu_j}J
]

---

## ⚙️ **3. Metode & Tahapan Implementasi**

### **A. Preprocessing & Feature Engineering**

* Ekstraksi durasi aktivitas
* One-hot encoding kolom kategori
* Transformasi fitur siklis (*hour, day, month → sin/cos*)
* Normalisasi **Yeo-Johnson**
* Penyaringan data noise (heartrate = 0)

### **B. K-Means dengan Steepest Descent**

1. Inisialisasi centroid secara random
2. Assign setiap titik ke centroid terdekat
3. Hitung WCSS
4. Hitung gradien untuk setiap centroid
5. Update centroid dengan Gradient Descent
6. Adaptasi learning rate ketika loss meningkat
7. Cek konvergensi

### **C. Evaluasi**

* Elbow Method
* Silhouette Score
* Visualisasi PCA 2D

---

## 🧪 **4. Parameter Utama**

| Parameter         | Nilai | Alasan                        |
| ----------------- | ----- | ----------------------------- |
| Learning rate (α) | 0.01  | Stabil, mencegah overshoot    |
| n_init            | 10    | Mengatasi minimasi non-convex |
| Tolerance         | 1e-6  | Konvergensi halus             |
| Loss Threshold    | 1e-3  | Mencegah iterasi berlebih     |

---

## 📊 **5. Hasil Utama**

### **Optimal number of clusters (k)**

Berdasarkan Elbow Method dan Silhouette Score, diperoleh:

👉 **k optimal = 4**

### **Loss Curve**

Loss turun stabil menuju konvergensi—menunjukkan update gradient descent berjalan efektif.

### **Visualisasi PCA**

Menunjukkan pemisahan cluster yang jelas antara aktivitas intensitas tinggi, rendah, dan campuran.

### **Interpretasi Cluster Singkat**

* **Cluster 0** — Short Distance Fast Activity
* **Cluster 1** — Long Distance Endurance
* **Cluster 2** — Casual Light Activity
* **Cluster 3** — High Performance Fast Activity

---


## 🧠 **6. Insight & Kesimpulan**

* Gradient Descent terbukti dapat digunakan sebagai alternatif update rule K-Means.
* Model stabil dan konvergen dengan adaptive learning rate.
* Cluster memberikan insight nyata terkait pola aktivitas dan intensitas pekerjaan.
* Pendekatan optimasi memberikan fleksibilitas lebih dibandingkan K-Means klasik.
