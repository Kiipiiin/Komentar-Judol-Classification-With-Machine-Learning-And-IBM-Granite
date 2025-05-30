# Komentar-Judol-Classification-With-Machine-Learning-And-IBM-Granite

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
Perbedaan Gaya Bahasa pada Komentar Promosi
1. Komentar promosi judi online memiliki ciri khas:
2. Ajakan & Urgensi: Menggunakan kalimat seperti "freebet 100rb", "buruan gas", "garansi 100%".
3. Nama Platform: Sering mencantumkan nama seperti "wisdomtoto", "pas4d", "meteorwin".
4. Penggunaan Simbol: Menggunakan @ dan # secara strategis.
5. Bahasa Promosi: Kata-kata seperti "gacor", "gratis", "newmember" mendominasi.

Pola Akun Pengguna
1. Repetisi Nama: Akun bot-like muncul berulang (e.g., Khokhar Saab, Gaming Boy).
2. Nama Mengandung Kata Kunci Judi: Seperti "@Indiaफूडी", "pas4d gacor".
3. Akun Normal: Seperti “Fitria Christalina” dan “arif ramadhan” tidak menunjukkan tanda spam.

Strategi Penyamaran dalam Komentar
1. Penggunaan Spasi & Simbol: "d3p0 100 jd 2jt buruan gas" atau "ketik di google wisdomtoto".
2. Pemisahan Kata Kunci: "pas4d" dan "gacor" ditulis terpisah untuk menghindari filter otomatis.
3. Kode Halus: Menggunakan instruksi tidak langsung seperti “ketik di google”.



