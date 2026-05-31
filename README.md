# EMNIST Letter Classification using HOG and SVM

## Deskripsi Proyek

Proyek ini merupakan implementasi klasifikasi huruf tulisan tangan menggunakan dataset **EMNIST Letters** dengan metode **Histogram of Oriented Gradients (HOG)** sebagai ekstraksi fitur dan **Support Vector Machine (SVM)** sebagai algoritma klasifikasi.

Model dilatih menggunakan fitur HOG yang diekstraksi dari citra huruf berukuran 28×28 piksel. Untuk memperoleh performa terbaik, dilakukan proses **Grid Search Cross Validation** pada parameter SVM.

---

## Informasi Mahasiswa

* **Nama** : Kemas Muhammad Irfan
* **NIM** : 4222311014
* **Kelas** : Robotika Malam A
* **Mata Kuliah** : Computer Vision (RE604)

---

## Dataset

Dataset yang digunakan adalah **EMNIST Letters Dataset** yang berisi citra huruf tulisan tangan dari alfabet A–Z.

Karena ukuran dataset cukup besar, file dataset tidak disertakan secara langsung di repository GitHub.

Format data:

* Kolom pertama : Label kelas (1–26)
* Kolom berikutnya : Nilai piksel citra 28×28

---

## Metode

### 1. Data Loading

Dataset dibaca menggunakan Pandas dan dipersiapkan untuk proses klasifikasi.

### 2. Data Balancing

Sebanyak 100 sampel dipilih dari setiap kelas sehingga distribusi data menjadi seimbang.

### 3. Feature Extraction

Ekstraksi fitur menggunakan metode **Histogram of Oriented Gradients (HOG)** dengan parameter:

* Orientations = 12
* Pixels per Cell = (8, 8)
* Cells per Block = (2, 2)
* Block Normalization = L2-Hys

### 4. Data Splitting

Dataset dibagi menjadi:

* Training Data = 80%
* Testing Data = 20%

Menggunakan:

```python
train_test_split(
    test_size=0.2,
    random_state=42,
    stratify=y
)
```

### 5. Model Training

Model menggunakan algoritma:

* Support Vector Machine (SVM)

Parameter terbaik dicari menggunakan:

* GridSearchCV
* 3-Fold Cross Validation

Parameter yang diuji:

```python
{
    'kernel': ['linear', 'rbf', 'poly'],
    'C': [0.1, 1, 10, 100],
    'gamma': ['scale', 'auto', 0.001, 0.01]
}
```

### 6. Evaluasi

Evaluasi dilakukan menggunakan:

* Accuracy
* Precision
* Recall
* F1-Score
* Classification Report
* Confusion Matrix

---

## Struktur Repository

```text
.
├── Data/
├── results/
│   ├── sample_dataset.png
│   └── summary_result.txt
├── emnist_hog_svm_classification.ipynb
├── emnist_hog_svm_classification.html
├── CV-Midterm-Project.pdf
└── README.md
```

---

## Output

Program menghasilkan:

* Visualisasi sampel dataset
* HOG feature extraction
* Training dan testing performance
* Classification report
* Confusion matrix
* Ringkasan hasil pada file `summary_result.txt`

---

## Cara Menjalankan

### Clone Repository

```bash
git clone https://github.com/kanaaavx/Computer-Vision-RE604.git
cd Computer-Vision-RE604
```

### Install Dependency

```bash
pip install numpy pandas matplotlib seaborn scikit-image scikit-learn
```

### Jalankan Notebook

Buka menggunakan:

* Jupyter Notebook
* Jupyter Lab
* Visual Studio Code

Kemudian jalankan seluruh cell secara berurutan.

---

## Catatan

GitHub saat ini gagal melakukan render preview notebook `.ipynb` dan menampilkan pesan **"An error occurred"** meskipun file notebook valid.

Sebagai alternatif, isi notebook dapat dilihat melalui file:

```text
emnist_hog_svm_classification.html
```

atau dibuka langsung menggunakan VS Code/Jupyter Notebook.

---

## Kesimpulan

Metode **HOG + SVM** berhasil digunakan untuk klasifikasi huruf tulisan tangan pada dataset EMNIST. Penggunaan Grid Search membantu menemukan parameter terbaik sehingga performa model menjadi lebih optimal.
