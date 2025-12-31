# README - Reproducibility Guide (Enron.ipynb)

Dokumen ini berisi panduan lengkap untuk memastikan **reprodusibilitas
eksperimen** pada notebook `Enron.ipynb`, mulai dari proses pengunduhan
dataset, kebutuhan environment, hingga cara menjalankan notebook dan
script secara konsisten di mesin lain.

------------------------------------------------------------------------

## ✅ Petunjuk Reprodusibilitas

Agar hasil eksperimen dapat direproduksi dengan baik, pastikan hal-hal
berikut dipenuhi:

1.  Menggunakan versi Python yang sama (minimal Python 3.8).
2.  Menggunakan dataset yang sama (**Enron Email Dataset dari Kaggle**).
3.  Menginstal seluruh library dengan versi yang kompatibel.
4.  Menjalankan seluruh sel notebook secara berurutan dari atas ke
    bawah.
5.  Tidak mengubah struktur folder proyek.

Struktur folder yang disarankan:

    /project-root
    │
    ├── Enron.ipynb
    ├── emails.csv
    ├── app_uas_final.py
    ├── xgb_model_final.pkl
    ├── iso_model_final.pkl
    └── README.md

------------------------------------------------------------------------

## 📥 Cara Download Dataset Kaggle

Notebook `Enron.ipynb` menggunakan **Enron Email Dataset** yang
disediakan melalui Kaggle.

### Langkah-langkah Download:

1.  Buka halaman dataset berikut:
    https://www.kaggle.com/wcukierski/enron-email-dataset

2.  Login ke akun Kaggle.

3.  Klik tombol **Download** (Ukuran ± 423 MB terkompresi).

4.  Ekstrak file hingga memperoleh file:

        emails.csv

5.  Pindahkan file `emails.csv` ke **folder yang sama** dengan
    `Enron.ipynb`.

Tanpa file `emails.csv`, notebook tidak akan dapat dijalankan.

------------------------------------------------------------------------

## 🧩 Persyaratan Library / Environment

Pastikan Python versi **3.8 atau lebih baru** telah terinstal.

Semua dependensi dapat diinstal dengan satu perintah berikut:

    pip install pandas numpy scikit-learn xgboost matplotlib seaborn nltk tqdm streamlit joblib

### Fungsi Utama Library:

-   `pandas`, `numpy` : Pemrosesan dan manipulasi data
-   `nltk` : Natural Language Processing (stopwords, tokenisasi)
-   `scikit-learn` : TF-IDF, Random Forest, Isolation Forest
-   `xgboost` : Model klasifikasi utama
-   `matplotlib`, `seaborn` : Visualisasi data
-   `tqdm` : Progress bar pemrosesan
-   `streamlit` : Dashboard SOC
-   `joblib` : Penyimpanan dan pemuatan model

Disarankan menggunakan **virtual environment**:

    python -m venv venv
    source venv/bin/activate    # Linux/Mac
    venv\Scripts\activate     # Windows

------------------------------------------------------------------------

## ▶️ Cara Menjalankan Notebook / Script untuk Reprodusibilitas

### 1. Menjalankan Notebook Training

Pastikan Anda berada di folder proyek yang berisi `Enron.ipynb` dan
`emails.csv`.

Jalankan perintah:

    jupyter notebook Enron.ipynb

Kemudian: 1. Buka file `Enron.ipynb` di browser. 2. Jalankan seluruh sel
**dari atas ke bawah secara berurutan**. 3. Proses ini akan: - Melakukan
preprocessing data - Melakukan training model - Menyimpan model ke file
`.pkl` - Membentuk file aplikasi `app_uas_final.py`

### 2. Menjalankan Aplikasi Hasil Training

Setelah proses training selesai:

    streamlit run app_uas_final.py

Aplikasi akan terbuka otomatis di browser dan siap digunakan sebagai
**SOC Dashboard**.

------------------------------------------------------------------------

## 🛑 Catatan Penting Reprodusibilitas

-   Jangan mengubah nama file:
    -   `emails.csv`
    -   `Enron.ipynb`
    -   `app_uas_final.py`
-   Jangan mengubah urutan eksekusi sel di notebook.
-   Pastikan environment bersih dari konflik versi library.
-   Jika terjadi error saat training:
    -   Periksa kembali versi Python
    -   Periksa apakah seluruh dependensi sudah terinstal dengan benar

------------------------------------------------------------------------

Dokumen ini dibuat untuk memastikan bahwa seluruh proses eksperimen
dapat diulang secara konsisten, dapat diuji oleh pihak lain, dan
memenuhi standar reprodusibilitas ilmiah.
