Proyek ini terdiri dari beberapa komponen utama:

Pra-pemrosesan Data
Ekstraksi Fitur
Penyeimbangan Data
Arsitektur Model
Alur Pelatihan
Evaluasi dan Pencatatan

1. Pra-pemrosesan Data
Gambar dikonversi ke grayscale dengan 3 channel
Diubah ukurannya menjadi 224x224 piksel (ukuran input ResNet18)
Dinormalisasi dengan mean dan std sebesar 0.5
Transformasi ini memastikan semua gambar memiliki format yang seragam

2. Ekstraksi Fitur

Memuat model ResNet18 yang sudah dilatih sebelumnya (pretrained)
Menghapus lapisan klasifikasi terakhir
Mengekstrak fitur dari dataset
Fitur yang diekstrak akan digunakan sebagai input untuk model klasifikasi

3. Penyeimbangan Data
SMOTE (Synthetic Minority Over-sampling Technique) diterapkan untuk menyeimbangkan dataset
Menghasilkan sampel sintetis untuk kelas minoritas
Memastikan representasi yang setara untuk semua kelas
Membagi data yang sudah seimbang menjadi data pelatihan (80%) dan pengujian (20%)
Stratifikasi digunakan untuk memastikan distribusi kelas yang seimbang

4. Arsitektur Model
Klasifikator terdiri dari:
Tiga lapisan fully connected
Fungsi aktivasi ReLU
Lapisan Dropout (rate 0.5) untuk regularisasi
Output layer sesuai dengan jumlah kelas sampah

5. Proses Pelatihan
Hyperparameter:

Learning rate: 1e-4 (kecepatan pembelajaran)
Batch size: 64 (jumlah sampel per batch)
Epochs: 50 (jumlah iterasi pelatihan)
Optimizer: AdamW (optimasi parameter model)
Loss function: CrossEntropyLoss (fungsi kerugian)

Alur pelatihan:

Forward pass melalui model
Menghitung loss (kerugian)
Backward pass dan optimisasi
Melacak metrik (loss, akurasi)
Evaluasi pada set pengujian
Mencatat hasil ke Weights & Biases

6. Evaluasi Model
Metrik evaluasi meliputi:
Loss pelatihan
Akurasi pelatihan
Akurasi pengujian
Matriks konfusi (confusion matrix)
Visualisasi distribusi kelas

Integrasi Weights & Biases
Proyek menggunakan Weights & Biases untuk pelacakan eksperimen

Mencatat hyperparameter
Melacak metrik pelatihan
Menyimpan artefak model
Memvisualisasikan matriks konfusi
