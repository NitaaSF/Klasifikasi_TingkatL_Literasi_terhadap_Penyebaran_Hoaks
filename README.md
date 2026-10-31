# Penerapan Metode K-Means untuk Klasifikasi Tingkat Literasi terhadap Penyebaran Hoaks di Jawa Barat

Proyek riset ini bertujuan untuk mengklasifikasikan Kabupaten/Kota di Provinsi Jawa Barat berdasarkan profil literasi, menganalisis tingkat kerentanan setiap klaster terhadap penyebaran berita hoaks, serta memvisualisasikan hasilnya secara interaktif melalui dashboard berbasis web.

---

## 📌 Pendahuluan

Penyebaran hoaks merupakan salah satu tantangan serius di era digital, khususnya di Provinsi Jawa Barat sebagai wilayah dengan populasi terbesar di Indonesia[cite: 10, 20]. Tingginya penetrasi internet yang tidak diimbangi dengan tingkat literasi digital dan pendidikan yang memadai memicu tingginya kerentanan masyarakat terhadap informasi palsu[cite: 10, 20].

Proyek ini memanfaatkan dataset sekunder (Open Data Jabar & Indeks Masyarakat Digital Indonesia) tahun 2022 untuk[cite: 10, 47]:
1. Mengelompokkan daerah di Jawa Barat berdasarkan 3 indikator literasi utama[cite: 10, 11].
2. Menganalisis tingkat kerentanan masing-masing klaster terhadap penyebaran hoaks[cite: 10, 11].
3. Menyajikan visualisasi spasial & 3D scatter plot dalam bentuk web dashboard interaktif[cite: 10, 11].

---

## 📊 Variabel Penelitian

Analisis K-Means Clustering dilakukan menggunakan 3 variabel utama[cite: 10, 11]:

* **IPLM (Indeks Pembangunan Literasi Masyarakat):** Menilai ketersediaan fasilitas, koleksi, dan tingkat kunjungan perpustakaan[cite: 10, 52].
* **Indeks Pendidikan:** Menggambarkan akses pendidikan berbasis Harapan Lama Sekolah (HLS) dan Rata-rata Lama Sekolah (RLS)[cite: 53].
* **IMDI (Indeks Masyarakat Digital Indonesia):** Mengukur infrastruktur, keterampilan digital, pemberdayaan, dan pekerjaan masyarakat digital[cite: 10, 53].

---

## 🛠️ Metodologi & Tahapan Analisis

1. **Pengumpulan Data:** Integrasi data dari Open Data Jabar dan portal Indeks Masyarakat Digital Indonesia[cite: 47].
2. **Preprocessing Data:**
   * Handling Missing Values (Imputasi/Cleaning)[cite: 49].
   * Standarisasi data menggunakan `StandardScaler` ($Z$-score normalization)[cite: 40, 54].
3. **Penentuan Jumlah Klaster Optimal ($k$):**
   * **Elbow Method:** Evaluasi penurunan nilai Inertia/WSS[cite: 41, 55].
   * **Silhouette Score:** Validasi kualitas pemisahan klaster[cite: 41, 55].
   * **Hasil optimal:** $k = 3$ (Klaster Rendah, Sedang, dan Tinggi)[cite: 55, 56].
4. **Klasterisasi & Evaluasi (K-Means):**
   * Perhitungan jarak Euclidean antar *data point* ke *centroid*[cite: 40, 41].
   * Evaluasi kualitas klaster menggunakan Silhouette Index[cite: 41, 42].
5. **Implementasi Web Dashboard:**
   * **Streamlit & Plotly:** Visualisasi 3D Scatter Plot interaktif, matriks statistik, dan peta Folium[cite: 64, 66].
   * **Tableau Public:** Visualisasi peta tematik (*Map Chart*), *Bar Chart*, dan *Pie Chart*[cite: 50, 61].

---

## 📈 Hasil Ringkasan Klastering

| Klaster | Jumlah Kab/Kota | Tingkat Kerentanan Hoaks | Karakteristik Wilayah |
| :--- | :---: | :---: | :--- |
| **Klaster 0 (Rendah)** | 9 Daerah | Tinggi | Seluruhnya daerah Kabupaten dengan IPLM & Indeks Pendidikan rendah[cite: 57, 58, 70]. |
| **Klaster 1 (Sedang)** | 11 Daerah | Sedang | Kebanyakan Kabupaten (termasuk Kota Banjar & Kota Cirebon) dengan nilai indeks menengah[cite: 57, 70]. |
| **Klaster 2 (Tinggi)** | 7 Daerah | Rendah | Seluruhnya daerah Kota (Kota Bandung, Depok, Bogor, dll.) dengan akses digital & literasi tinggi[cite: 58, 70]. |

---

## 📁 Struktur Direktori

```text
.
├── data/
│   ├── dataset_project2_new.xlsx    # Dataset utama (IPLM, Indeks Pendidikan, IMDI)
│   ├── kota.geojson                 # Data peta batas wilayah Jawa Barat
│   └── hasil_clustering.xlsx        # Output data setelah klasterisasi
├── notebooks/
│   └── kmeans_analysis.ipynb        # Experimentation, Elbow, & Silhouette Score
├── app.py                           # Application script (Streamlit Dashboard)
├── README.md                        # Dokumentasi proyek
└── requirements.txt                 # Requirements & dependencies

🚀 Cara Menjalankan Dashboard (Streamlit)

Kloning Repositori
git clone https://github.com/username/kmeans-literasi-hoaks-jabar.git

cd kmeans-literasi-hoaks-jabar

2. Setup Virtual Environment

python -m venv venv

# Windows

venv\Scripts\activate

# Linux/macOS

source venv/bin/activate

3. Instal Dependencies

pip install -r requirements.txt

4. Jalankan Aplikasi Streamlit

streamlit run app.py

👨‍💻 Tim Peneliti

Gilang Al Raffi (NPM: 184220002) - S1 Sains Data, Universitas Logistik dan Bisnis Internasional
Nita Sawalia Fitri (NPM: 184220024) - S1 Sains Data, Universitas Logistik dan Bisnis Internasional
Dosen Pembimbing: Kiki Mustaqim, S.Si., M.Si.
Penguji Utama: Noviana Riza, S.Si., M.T.
Koordinator Proyek: Woro Isti Rahayu, S.T., M.T., SFPC.
📜 Lisensi

Proyek ini dilindungi di bawah lisensi MIT. Lihat file LICENSE untuk informasi lebih detail.
