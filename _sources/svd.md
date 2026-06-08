# Proyek Komputasi Aljabar Linier Interaktif: SVD Eigenface & Animasi Transformasi Geometri

Repositori ini berisi dokumentasi dan implementasi kode program interaktif untuk dua topik utama dalam praktikum Aljabar Linier: Rekognisi Wajah Berbasis **Singular Value Decomposition (SVD)** dan Animasi Interaktif **Transformasi Geometri (Refleksi)**.

---

## 🔗 Link Akses Google Colab
Seluruh program di bawah ini dapat dijalankan secara interaktif dengan antarmuka berbasis *GUI Form Fields* melalui tautan berikut:
👉 **[Notebook Google Colab - Proyek Aljabar Linier Interaktif](https://colab.research.google.com/drive/1_1hXeEx-2mbcqy2w4lCcM62-dSDkb1eL?usp=sharing)**

---

## 📑 Bagian 1: Pengenalan Wajah Berbasis SVD (Sistem Kontrol Eigenface)

### 1. Landasan Teori Matematika SVD
Singular Value Decomposition (SVD) adalah metode faktorisasi yang memecah matriks data utama $A$ (berdimensi $m \times n$) menjadi perkalian tiga matriks terpisah:

$$A = U \Sigma V^T$$

Dalam proyek ini, matriks data dikondisikan secara asimetris berdasarkan database riil yang terdiri dari **30 foto wajah** (20 sampel *male* dan 10 sampel *female*).
* **Matriks $A$ ($35.000 \times 30$):** Setiap kolom mewakili satu buah gambar wajah yang telah diratakan (*flattened*) dari dimensi asli $200 \times 175$ piksel menjadi vektor kolom tunggal sepanjang $35.000$ baris.
* **Matriks $U$ ($35.000 \times 30$):** Matriks ortonormal left singular vectors yang merepresentasikan **Eigenfaces** ("wajah hantu"). Kolom pertama ($U_1$) memuat varians komponen paling dominan (seperti arah pencahayaan makro global), sedangkan kolom lebih besar (misalnya kolom 7) menangkap fitur detail mikro yang lebih spesifik.
* **Matriks $\Sigma$ ($30 \times 30$):** Matriks diagonal persegi yang menampung nilai singular ($\sigma_i$) terurut dari besar ke kecil, di mana kuadrat nilai singular tersebut setara dengan nilai karakteristik Eigenvalue ($\lambda_i = \sigma_i^2$).
* **Matriks $V^T$ ($30 \times 30$):** Matriks right singular vectors yang menampung koefisien koordinat proyeksi data wajah asli ke dalam ruang bagian (*Eigenspace*).

### 2. Fitur Operasional Menu Interaktif
Sistem operasi pada notebook dilengkapi dengan parameter kontrol yang dapat diubah secara langsung tanpa memodifikasi kode program:
* **`PILIH_MODE`**: Mengontrol sumber data matriks $A$, baik menggunakan `MODE FOTO ASLI` (mengunduh otomatis 30 database file fisik `.jpg` dari server GitHub) atau `MODE SIMULASI` (membangun pola matriks tiruan berbasis fungsi gelombang sinus-kosinus).
* **`PILIH_MENU`**: Membuka 6 variasi menu analisis (Cek ukuran ordo, ekstraksi nilai singular, visualisasi grafik gambar komponen Eigenface lewat `plt.imshow`, hingga uji tebakan klasifikasi gender foto baru menggunakan perhitungan **Jarak Euclidean** terpendek dari koordinat *centroid* kelompok).

---

## 📑 Bagian 2: Animasi Interaktif Transformasi Geometri (Refleksi)

### 1. Representasi Matriks Transformasi 2D
Program kedua menerapkan konsep transformasi linier dua dimensi pada objek geometri poligon. Proses pemetaan titik asal $(x, y)$ menuju koordinat bayangan hasil pencerminan $(x', y')$ dikalkulasikan menggunakan perkalian matriks standar berikut:

* **Pencerminan Terhadap Sumbu X:**
  $$\begin{bmatrix} x' \\ y' \end{bmatrix} = \begin{bmatrix} 1 & 0 \\ 0 & -1 \end{bmatrix} \begin{bmatrix} x \\ y \end{bmatrix} \rightarrow (x', -y')$$
* **Pencerminan Terhadap Sumbu Y:**
  $$\begin{bmatrix} x' \\ y' \end{bmatrix} = \begin{bmatrix} -1 & 0 \\ 0 & 1 \end{bmatrix} \begin{bmatrix} x \\ y \end{bmatrix} \rightarrow (-x', y')$$
* **Pencerminan Terhadap Garis $y = x$:**
  $$\begin{bmatrix} x' \\ y' \end{bmatrix} = \begin{bmatrix} 0 & 1 \\ 1 & 0 \end{bmatrix} \begin{bmatrix} x \\ y \end{bmatrix} \rightarrow (y', x)$$
* **Pencerminan Terhadap Garis $y = -x$:**
  $$\begin{bmatrix} x' \\ y' \end{bmatrix} = \begin{bmatrix} 0 & -1 \\ -1 & 0 \end{bmatrix} \begin{bmatrix} x \\ y \end{bmatrix} \rightarrow (-y', -x)$$
* **Pencerminan Terhadap Titik Pusat $(0,0)$:**
  $$\begin{bmatrix} x' \\ y' \end{bmatrix} = \begin{bmatrix} -1 & 0 \\ 0 & -1 \end{bmatrix} \begin{bmatrix} x \\ y \end{bmatrix} \rightarrow (-x', -y')$$

### 2. Catatan Teknis Dokumentasi Kode (*Debugging*)
* **Sinkronisasi Node Penutup Poligon:** Untuk membuat bangun datar yang menutup sempurna, koordinat titik pertama diduplikasi ke bagian paling akhir indeks array. Logika fungsi `on_drag` memastikan bahwa apabila titik dasar pertama (`indeks 0`) digeser posisinya oleh mouse, maka elemen array terakhir (`indeks [-1]`) otomatis ikut terbarui agar rangkaian garis objek tidak terputus.
* **Keterbatasan Lingkungan Kerja Cloud:** Karena program ini menggunakan interaksi klik-seret mouse dinamis secara *real-time* berbasis modul `FuncAnimation` dan event manager dari backend **`TkAgg`**, kode refleksi interaktif ini **wajib dijalankan di terminal lokal komputer (seperti VS Code atau PyCharm)**. Lingkungan web Google Colab tidak mendukung *rendering* pop-up jendela GUI interaktif Tkinter dari server cloud mereka.
