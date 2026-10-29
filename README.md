# Prescriptive Data Science - Smart Portfolio Optimizer

## 1. Deskripsi Proyek

**Smart Portfolio Optimizer** adalah proyek analisis data untuk membantu menyusun portofolio saham di pasar modal Indonesia. Proyek ini menggabungkan tiga pendekatan utama, yaitu **Descriptive Analytics, Predictive Analytics, dan Prescriptive Analytics**, untuk memahami karakteristik saham, menganalisis potensi pergerakan harga, serta menentukan alokasi investasi yang optimal berdasarkan risiko dan imbal hasil.

## 2. Tujuan Proyek

- Menganalisis kinerja, risiko, dan hubungan antar saham.
- Membangun model prediksi untuk memperkirakan pergerakan imbal hasil saham.
- Membandingkan beberapa strategi pembentukan portofolio.
- Menentukan alokasi investasi dengan mempertimbangkan risiko, imbal hasil, dan biaya transaksi.
- Menguji kinerja strategi melalui simulasi historis.

## 3. Data yang Digunakan

Data mencakup **50 saham Indonesia** dengan periode historis 3 Januari 2022 hingga 31 Agustus 2026, yang diperoleh melalui Yahoo Finance.

Data utama meliputi:
- `stock_master`: informasi dasar saham.
- `historical_prices`: data historis harga saham.

Setelah proses pemeriksaan kualitas data dan penyaringan saham, terdapat **28 saham** yang digunakan dalam analisis lanjutan.

## 4. Metodologi

### A. Descriptive Analytics

Tahap ini digunakan untuk memahami karakteristik data saham melalui:
- Analisis imbal hasil dan volatilitas.
- Analisis korelasi antar saham.
- Analisis berdasarkan sektor.
- Perhitungan skor faktor untuk membantu mengevaluasi saham.

### B. Predictive Analytics

Tahap ini bertujuan menganalisis kemampuan model dalam memprediksi imbal hasil saham. Model yang digunakan meliputi:
- Linear Regression.
- Ridge Regression.
- Random Forest.

Fitur yang digunakan mencakup imbal hasil historis, rata-rata bergerak, dan volatilitas bergulir. Evaluasi model dilakukan menggunakan MAE, RMSE, akurasi arah pergerakan, dan Information Coefficient (IC).

Pengujian juga membandingkan pelatihan statis dengan pendekatan *monthly walk-forward*.

### C. Prescriptive Analytics

Tahap ini digunakan untuk menentukan alokasi portofolio berdasarkan sejumlah strategi:
- Equal Weight.
- Market Capitalization Weight.
- Minimum Variance.
- Risk Parity / Equal Risk Contribution (ERC).
- Blend Equal Weight dan ERC.
- Maximum Sharpe Ratio.

Estimasi risiko menggunakan metode Ledoit-Wolf dan EWMA, kemudian dikombinasikan untuk membantu proses optimasi.

Optimasi dilakukan dengan SLSQP menggunakan batasan berikut:
- Portofolio hanya memiliki posisi beli (*long-only*).
- Bobot maksimal setiap saham sebesar 10%.
- Bobot maksimal setiap sektor sebesar 35%.
- Total bobot portofolio harus berjumlah 100%.

Kinerja strategi diuji melalui simulasi *walk-forward* bulanan dengan mempertimbangkan biaya transaksi dan turnover.

## 5. Hasil Utama

- Dari 50 saham awal, sebanyak 28 saham lolos proses penyaringan.
- Sinyal prediksi yang dihasilkan model masih relatif lemah.
- Biaya transaksi dan turnover dapat mengurangi keuntungan strategi.
- Dalam pengujian *walk-forward* selama 32 bulan, strategi optimasi yang diuji tidak mengungguli Equal Weight berdasarkan Sharpe Ratio.
- Kombinasi **50% Equal Weight dan 50% ERC** dipilih sebagai pendekatan portofolio utama karena memberikan volatilitas yang sedikit lebih rendah, turnover yang rendah, serta hasil positif pada kedua periode pengujian.
- Dengan modal Rp10.000.000, keterbatasan pembelian minimal satu lot membuat investasi hanya dapat dialokasikan ke 18 dari 28 saham.

## 6. Teknologi dan Library

- Python
- Pandas dan NumPy
- Scikit-learn
- SciPy
- Matplotlib dan Seaborn
- Yahoo Finance

## 7. Output Proyek

Proyek menghasilkan sejumlah output untuk mendukung analisis dan evaluasi, antara lain:
- Bobot akhir portofolio.
- Alokasi investasi berdasarkan modal Rp10.000.000.
- Metrik kinerja *walk-forward*.
- Evaluasi sinyal prediktif.
- Hasil eksperimen strategi.
- Pemeriksaan kewajaran hasil optimasi.

Nama file output mengikuti hasil yang dihasilkan oleh notebook.

## 8. Keterbatasan

- Hasil analisis historis tidak menjamin kinerja investasi di masa depan.
- Analisis terbatas pada saham dan periode data yang digunakan.
- Biaya transaksi, slippage, likuiditas, dan pajak belum sepenuhnya mencerminkan seluruh kondisi pasar nyata.
- Pemilihan faktor dan asumsi model dapat memengaruhi hasil optimasi.
- Pandangan investasi Black-Litterman yang menggunakan data Oktober 2026 belum diuji dalam simulasi *walk-forward*.

## 9. Kesimpulan

Proyek ini menunjukkan bagaimana analisis deskriptif, prediktif, dan preskriptif dapat digabungkan untuk mendukung pengambilan keputusan investasi. Berdasarkan hasil pengujian, model prediksi belum menunjukkan sinyal yang cukup kuat untuk secara konsisten mengungguli strategi Equal Weight. Oleh karena itu, kombinasi Equal Weight dan ERC digunakan sebagai pendekatan portofolio utama dengan mempertimbangkan diversifikasi, risiko, dan turnover.

**Catatan:** Proyek ini merupakan analisis akademik dan bukan rekomendasi investasi.
