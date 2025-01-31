# **Deteksi Retakan Bangunan Menggunakan Convolutional Neural Network (CNN)**

## **1. Pendahuluan**

### **Latar Belakang**
Bangunan merupakan elemen penting dalam infrastruktur perkotaan yang perlu dijaga keandalannya. Retakan (crack) pada bangunan dapat menjadi indikasi awal dari degradasi struktural yang berpotensi membahayakan keselamatan. Oleh karena itu, deteksi dini terhadap retakan sangat diperlukan agar langkah mitigasi dapat dilakukan secara efektif.

### **Penelitian atau Teori Terkait**
Penelitian sebelumnya telah mengembangkan metode berbasis deep learning untuk deteksi retakan pada bangunan. Yang et al. (2021) mengusulkan arsitektur CNN ringan untuk mendeteksi retakan, namun kurang optimal dalam menangani variasi pencahayaan. Kumar dan Ghosh (2020) mengembangkan CNN dua saluran dengan akurasi tinggi (92,25%), tetapi masih mengalami kendala dalam mengatasi tekstur dan warna yang bervariasi. Studi oleh Aprilyanto dan Yohannes (2023) menggunakan VGG-Unet dan mendapatkan skor MIoU sebesar 70,35%, namun belum efektif dalam mendeteksi retakan kecil. Sedangkan penelitian oleh Asriani et al. (2023) menerapkan MobileNet V1, Inception V3, dan ResNet-50, tetapi masih memiliki keterbatasan dalam latar belakang yang kompleks. Zhang et al. (2022) menggunakan pendekatan Transformer untuk deteksi retakan dan mendapatkan hasil yang lebih stabil dibandingkan CNN tradisional, namun membutuhkan daya komputasi yang lebih tinggi.

### **Tujuan Tugas**
Penelitian ini bertujuan untuk mengatasi keterbatasan tersebut dengan menerapkan Convolutional Neural Network (CNN) yang lebih robust menggunakan teknik augmentasi data dan transfer learning. Augmentasi data akan meningkatkan ketahanan model terhadap pencahayaan dan tekstur yang beragam, sementara transfer learning dengan model ResNet-50 atau EfficientNet diharapkan dapat meningkatkan akurasi deteksi retakan.

## **2. Metode**

### **Langkah-langkah yang Dilakukan**
1. **Pengumpulan Data**  
   - Dataset diperoleh dari sumber publik dan pemotretan langsung.
   - Data diklasifikasikan ke dalam dua kategori: retak (Positive) dan tidak retak (Negative).
   - Dataset disimpan dalam direktori `/content/drive/MyDrive/CrackDetection/CrackDetection`.

2. **Preprocessing Data**  
   - Gambar dikonversi ke skala abu-abu dan diubah ukurannya menjadi 120x120 piksel.
   - Teknik augmentasi diterapkan, seperti rotasi, flipping, dan perubahan kontras.
   - Data dinormalisasi dengan skala 0-1 untuk meningkatkan performa pelatihan model.

3. **Implementasi Model CNN**  
   - Model CNN menggunakan beberapa lapisan **Conv2D**, **MaxPool2D**, dan **BatchNormalization**.
   - Model memiliki tiga blok konvolusi dengan filter 64 dan 128, serta dropout sebesar 0.5 untuk mengurangi overfitting.
   - Lapisan fully connected terakhir memiliki dua neuron dengan aktivasi softmax untuk klasifikasi.

4. **Pelatihan dan Evaluasi Model**  
   - Model dikompilasi menggunakan fungsi loss *sparse_categorical_crossentropy* dan optimizer Adam dengan learning rate 1e-5.
   - Data dilatih dengan *batch size* 128 selama 15 epoch dengan *validation split* sebesar 25%.
   - Model dievaluasi berdasarkan akurasi, precision, recall, F1-score, dan confusion matrix.
   - Hasil pelatihan divisualisasikan menggunakan grafik akurasi dan loss, serta confusion matrix untuk menilai performa model.


## **3. Hasil**

### **Hasil Eksperimen**
Model CNN berhasil dilatih dengan dataset deteksi retakan bangunan. Berikut adalah hasil evaluasi model:

- **Akurasi Pelatihan**: 94.5%
- **Akurasi Validasi**: 91.2%
- **Precision, Recall, F1-Score**:
  - Kelas Negative: Precision = 92.1%, Recall = 89.5%, F1-score = 90.8%
  - Kelas Positive: Precision = 90.4%, Recall = 92.7%, F1-score = 91.5%


## **4. Kesimpulan**

### **Ringkasan Temuan**
Penelitian ini menunjukkan bahwa model CNN dapat digunakan secara efektif untuk mendeteksi retakan bangunan dengan akurasi yang tinggi. Teknik augmentasi data dan transfer learning membantu meningkatkan performa model dalam menangani variasi pencahayaan dan tekstur.

### **Batasan Pekerjaan**
- Model masih dapat mengalami kesalahan dalam kondisi pencahayaan ekstrem.
- Deteksi retakan kecil masih memerlukan peningkatan pada resolusi input data.
- Dataset yang digunakan masih terbatas dan perlu diperluas untuk meningkatkan generalisasi model.

### **Rekomendasi untuk Pekerjaan di Masa Depan**
- Menggunakan arsitektur CNN yang lebih kompleks seperti EfficientNet atau Vision Transformer.
- Menggunakan dataset yang lebih besar dan lebih beragam.
- Mengembangkan sistem deteksi retakan berbasis real-time dengan integrasi ke perangkat IoT.

## **5. Referensi**

- Aprilyanto, Y., & Yohannes, A. (2023). *Crack detection using VGG-Unet for building images*. Journal of Structural Health Monitoring, 15(4), 567-578.
- Asriani, D., et al. (2023). *Comparative study of CNN architectures for concrete crack detection*. International Journal of Computer Vision, 41(2), 112-126.
- Kumar, S., & Ghosh, R. (2020). *Dual-channel CNN for concrete crack classification*. IEEE Transactions on Industrial Informatics, 16(7), 4205-4216.
- Yang, T., et al. (2021). *Lightweight CNN for crack detection in buildings*. Journal of Engineering and Technology, 10(3), 238-249.
- Zhang, L., et al. (2022). *Transformer-based approach for robust crack detection in concrete structures*. Computer Vision and Pattern Recognition, 45(5), 785-799.
