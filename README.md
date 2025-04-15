# Proyek Analisis Sentimen Ulasan Aplikasi TIX ID
Proyek ini bertujuan untuk menganalisis sentimen pengguna terhadap aplikasi TIX ID dengan mengolah ulasan yang diperoleh melalui web scraping dari Google Play Store. Analisis ini berfokus pada ulasan berbahasa Indonesia untuk mengidentifikasi sentimen positif dan negatif. Berbagai model deep learning diuji untuk memprediksi sentimen dari teks ulasan pengguna TIX ID.

## Deskripsi Dataset
Dataset yang digunakan adalah `ulasan_TIXID.csv` yang mencakup informasi sebagai berikut:
- **comment**: teks ulasan pengguna aplikasi TIX ID
- **rating**: rating yang diberikan oleh pengguna (1-5)
- **thumbsUpCount**: seberapa banyak pengguna lain yang menganggap ulasan tersebut bermanfaat atau relevan
- **at**: memberikan informasi waktu dan tanggal kapan pengguna memberikan ulasan terhadap aplikasi TIX ID

## Tahapan Pengolahan Analisis Sentimen

### 1. **Loading Dataset**
Dataset dimuat menggunakan `pandas` untuk melihat informasi tentang jumlah baris, kolom, dan tipe data.

### 2. **Pra-pemrosesan Dataset**
- Mengubah tipe data pada kolom 'at' menjadi datetime
- Menghapus missing values (nilai yang kosong)
- Menghapus data duplikat

### 3. **Preprocessing Text**
- **Cleaning Text**: menghapus karakter khusus, tanda baca, dan angka yang tidak relevan
- **Case Folding**: mengubah semua teks menjadi huruf kecil agar konsisten
- **Tokenizing Text**: membagi teks ulasan menjadi kata per kata atau frasa
- **Filtering Text**: menghapus kata-kata umum (stop words) yang tidak memberikan makna penting
- **Stemming Text**: mengubah kata menjadi bentuk dasar
- **Remove Emoji**: menghapus emoji yang tidak memberikan makna penting 
- **Slang Words Manual**: menyesuaikan kata-kata gaul/slang dalam teks ulasan agar sesuai dengan kata baku atau makna sebenarnya
- **Menggabungkan Teks**: menggabungkan semua proses di atas ke dalam satu kolom baru

### 4. Pelabelan
Pada tahapan ini, pemberian label [positif](https://raw.githubusercontent.com/angelmetanosaa/dataset/main/lexicon_positive.csv) dan [negatif](https://raw.githubusercontent.com/angelmetanosaa/dataset/main/lexicon_negative.csv) pada data ulasan berdasarkan pada repository github milik orang lain. Kemudian dilakukan visualisasi kata wordcloud baik secara umum, positif maupun negatif serta visualisasi dataset.

### 5. Modelling Algoritma Deep Learning
Pada tahapan ini, digunakan ekstraksi fitur tokenizer kemudian encode labes ke format numerik pada berbagai algoritma deep learning dan variasi data splitting. Rincian sebagai berikut:
- Model 1: LSTM (70/30 Split)
- Model 2: RNN (70/30 Split)
- Model 3: CNN (80/20 Split)
- Model 4: GRU (80/20 Split)

### 6. Prediksi
Pada tahapan ini, digunakan algoritma LSTM sebagai model utama karena memiliki validation accuracy sebesar 88,65% untuk memprediksi kalimat baru apakah memiliki sentimen positif atau negatif.
  
