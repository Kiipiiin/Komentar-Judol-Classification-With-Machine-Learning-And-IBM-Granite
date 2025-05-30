# Komentar-Judol-Classification-With-Machine-Learning-And-IBM-Granite

LINK COLAB NOTEBOOK: https://colab.research.google.com/drive/1g7LDQ7MTomjGSdtRfSynqzjPlojpojRO?usp=sharing
# Project Overview
Latar Belakang:
Perkembangan live streaming sebagai media interaksi publik kini menghadapi tantangan baru: penyalahgunaan oleh akun-akun anonim untuk menyebarkan promosi judi online. Fenomena ini terjadi bahkan dalam acara budaya yang bersifat resmi dan publik

Tujuan Proyek:
Menganalisis dan mendeteksi komentar yang mengandung promosi judi online dalam siaran langsung YouTube acara budaya publik, serta menggali pola dan strategi penyamaran komentar-komentar tersebut menggunakan bantuan AI, baik melalui model klasifikasi tradisional maupun Large Language Model (LLM).

Pendekatan:
1. Preprocessing dan klasifikasi komentar menggunakan model final XGBoost supaya sudah ada pipeline dasar dan bisa dideploy dan digunakan untuk memoderasi komentar di waktu nyata.
2. Analisis semantik dan summarization komentar menggunakan IBM Granite LLM.
3. Penarikan insight berdasarkan perbedaan gaya bahasa, strategi spam, dan narasi dominan dalam komentar.

# Raw Dataset
Deskripsi Dataset: Deteksi Judi Online (https://www.kaggle.com/datasets/yaemico/deteksi-judi-online)
Judul: 🔴LIVE Wayang Jogja Night Carnival #9, Perayaan HUT ke-268 Kota Yogyakarta
Channel: @TribunJogjaOfficial
Sumber: YouTube

Deskripsi:
Dataset ini berisi komentar yang diambil dari siaran langsung "Wayang Jogja Night Carnival #9" yang diselenggarakan dalam rangka merayakan HUT ke-268 Kota Yogyakarta. Komentar dikumpulkan dari video tersebut untuk menganalisis dan mendeteksi promosi judi online dalam interaksi live streaming.
Fitur:
1. datetime: Waktu komentar ditulis.
2. author_name: Nama pengguna yang menulis komentar.
2. message: Isi asli komentar.
4. cleaned_message: Versi komentar yang telah dibersihkan.
5. label: Label biner (0 = non-promosi, 1 = promosi judi online).

# Insight & Findings
Perbedaan Gaya Bahasa pada Komentar Promosi, Komentar promosi judi online memiliki ciri khas:
1. Ajakan & Urgensi: Menggunakan kalimat seperti "freebet 100rb", "buruan gas", "garansi 100%".
2. Nama Platform: Sering mencantumkan nama seperti "wisdomtoto", "pas4d", "meteorwin".
3. Bahasa Promosi: Kata-kata seperti "gacor", "gratis", "newmember" mendominasi.

Pola Akun Pengguna
1. Repetisi Nama: Akun bot-like muncul berulang (e.g., Khokhar Saab, Gaming Boy).
2. Nama Mengandung Kata Kunci Judi: Seperti "@Indiaफूडी", "pas4d gacor".
3. Akun Normal: Seperti “Fitria Christalina” dan “arif ramadhan” tidak menunjukkan tanda spam.

Strategi Penyamaran dalam Komentar
1. Penggunaan Spasi & Simbol: "d3p0 100 jd 2jt buruan gas" atau "ketik di google wisdomtoto".
2. Pemisahan Kata Kunci: "pas4d" dan "gacor" ditulis terpisah untuk menghindari filter otomatis.
3. Kode Halus: Menggunakan instruksi tidak langsung seperti “ketik di google”.

Narasi Dominan Promosi Judi
1. Tema Freebet: >60% menggunakan "freebet 100rb" atau sejenisnya.
2. Link Promosi Terselubung: Komentar menyuruh pengguna mencari di Google.
3. Jaminan Menang: Sering menawarkan janji seperti “garansi 100%”.

Analisis False Positive
Komentar Non-promosi: Seperti "selamat ulang tahun jogja ku tercinta".
Kesalahan Klasifikasi: Komentar seperti “pas4d gacor” tergolong ambigu, karena menyebut platform tapi tanpa ajakan langsung.

# AI Support Explanation
Dalam proyek ini digunakan kombinasi model Machine Learning dan LLM Granite:
1. Model Klasifikasi (XGBoost)  
   - **Tujuan**: Mendeteksi komentar berlabel promosi judi secara otomatis.  
   - **Input**: Komentar yang telah dibersihkan.  
   - **Output**: Label klasifikasi (0 atau 1).

2. LLM IBM Granite (granite-3.3-8b-instruct)  
   - **Tujuan**: Menganalisis semantik komentar terklasifikasi.  
   - **Teknik**: Prompt injection berisi:

     ```python
     prompt = f"""
     Kamu adalah pakar linguistik digital dan analis keamanan siber yang bertugas mengidentifikasi pola bahasa dan strategi penyamaran dalam komentar promosi judi online.
     Tim kita sudah membuat model XGBoost dan akan mengirim anda hasil klasifikasinya dengan format (Username: Komentar).

     Berikut ini adalah hasil klasifikasi komentar promosi judi online:
     {judi_text}

     Berikut ini adalah hasil klasifikasi komentar non-promosi:
     {nonjudi_text}
     """
     ```
   - **Output**:  
     Ringkasan pola bahasa, narasi dominan, dan strategi spam, seperti:
     - Kata-kata ajakan *(gratis, freebet, gacor)*  
     - Penggunaan nama akun yang mirip bot  
     - Teknik manipulasi simbolik seperti *“@”* dan *“ketik di google”*

# Conclusion & Recommendation
Dampak Nyata: Komentar promosi judi dapat mengganggu ruang publik virtual dan menciptakan persepsi negatif terhadap acara budaya.

Solusi: Kombinasi sistem klasifikasi otomatis dan analisis LLM dapat digunakan untuk memoderasi komentar di waktu nyata.

Rekomendasi: Platform streaming dan penyelenggara acara publik digital perlu mengadopsi AI moderasi sebagai sistem pertahanan terhadap penyalahgunaan platform.







