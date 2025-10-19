# Klasifikasi Genre Lirik Lagu Menggunakan Inferensi LLM (Granite)

## Project Overview
Proyek ini bertujuan untuk menganalisis dan mengklasifikasikan 1100 data lirik lagu (dari total 2199 data set yang seharusnya di uji) ke dalam empat genre utama (Pop, Rock, Rap, Country). Klasifikasi dilakukan menggunakan Large Language Model (LLM) dari IBM, yaitu **Granite**, dengan menerapkan teknik *Few-Shot Learning*.

Tantangan utama proyek ini adalah mengatasi ketidakstabilan koneksi internet (Wi-Fi) dan keterbatasan unit komputasi/kredit API, yang diatasi dengan penerapan metodologi Batch Processing atau checkpointing.

## Raw Dataset Link
https://www.kaggle.com/datasets/kristianperriu/genereclassification

## Insight & Findings (Analisis Kunci)
### Analytical Result & Akurasi Final
Proyek ini diselesaikan dengan menguji 1100 data bersih (setelah menghapus X data *corrupt*) dan mencapai akurasi keseluruhan sebesar **63.17%**.

### Temuan (Findings) Kunci
* **Akurasi Solid:** Akurasi **63.17%** jauh melampaui tebakan acak (25%), memvalidasi efektivitas LLM untuk tugas klasifikasi multi-kelas.
* **Performa Terbaik**: Genre Rap dan Rock mencapai skor Precision tertinggi (92.1% dan 91.7%). Hal ini menunjukkan bahwa liriknya memiliki ciri linguistik yang paling spesifik dan unik, sehingga ketika model mengidentifikasi ciri khas ini, hasilnya sangat akurat.
* **Kebingungan Kritis:** Kesalahan terbesar (Confusion) terjadi antara Rock dan Pop, serta antara Country dan Pop (Pop sering menjadi output yang salah). Model sering memprediksi lirik Rock dan Country sebagai Pop karena adanya tumpang tindih tema lirik romansa, gaya naratif, atau lirik umum yang mirip di antara genre-genre tersebut.

## AI Support Explanation
Model yang digunakan adalah **LLM Granite** dari IBM, yang dijalankan melalui API Replicate.

* **Teknik:** Kami menggunakan teknik Few-Shot Learning dengan menyediakan 8 contoh lirik (2 per genre) langsung di dalam *prompt* untuk membimbing model dalam format dan gaya klasifikasi.
* **Prompt Engineering:** *Prompt* dirancang khusus untuk memaksa model memberikan output hanya dalam format genre yang diminta, sehingga mengurangi output yang tidak valid.

## Conclusion & Recommendation
* **Conclusion:** LLM dapat digunakan sebagai *tools* yang andal untuk *tagging* dan analisis konten musik.
* **Recommendation:** Untuk meningkatkan akurasi, disarankan melakukan Post-Processing atau penyempurnaan prompt pada lirik yang memiliki ciri Rock atau Country tetapi diprediksi sebagai Pop. Hal ini dapat dilakukan dengan menambahkan kriteria spesifik di prompt yang berfokus pada struktur lirik, diksi, atau penggunaan bahasa non-formal untuk membedakan secara lebih tegas antara genre yang tumpang tindih.
