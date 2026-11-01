# Gold Signal AI — Android Prototype 0.1.0

Aplikasi Android pribadi untuk analisis XAU/USD dengan H1, M5, M1; EMA 20/200; level support/resistance; kandidat entry, SL, TP1/TP2; dan kalkulator batas risiko nominal. Eksekusi trading tetap manual di HFM MT5.

## Status penting
- Ini adalah prototipe kode, bukan APK yang sudah dikompilasi atau aplikasi siap produksi.
- Versi awal mengambil data ketika tombol ditekan; belum ada streaming/polling otomatis di latar belakang.
- API key dibutuhkan. Dukungan `XAU/USD`, interval `1min`, `5min`, `1h`, kuota, serta ketentuan data real-time bergantung pada paket Twelve Data dan harus diuji dengan akun pengguna.
- Harga provider dapat berbeda dari bid/ask dan spread HFM.
- Logika sinyal adalah aturan teknikal sederhana, bukan strategi yang sudah terbukti menguntungkan.
- Kalkulator risiko hanya menghitung nominal risiko dari saldo dan persentase. Estimasi risiko berdasarkan lot belum dihitung karena perlu spesifikasi kontrak/tick value HFM yang sesuai jenis akun.

## Cara membuka dan menjalankan
1. Instal Android Studio di komputer.
2. Ekstrak ZIP ini.
3. Android Studio → Open → pilih folder `GoldSignalAI_Android`.
4. Tunggu Gradle Sync. Gunakan JDK 17 dan Android SDK 35.
5. Jalankan pada emulator atau HP Android dengan USB debugging.
6. Daftar/masuk ke Twelve Data, buat API key, masukkan di aplikasi.
7. Tekan **Ambil data & analisis**.

## Cara kerja sinyal
- H1 bullish jika harga terakhir > EMA20 > EMA200; bearish jika harga terakhir < EMA20 < EMA200.
- M5 menggunakan aturan searah yang sama untuk setup.
- M1 mengonfirmasi arah berdasarkan posisi harga terhadap EMA20.
- Jika semua timeframe tidak searah, aplikasi menampilkan `NO TRADE`.
- Support/resistance diambil dari low/high 20 candle M5 terakhir.
- SL dan target dihitung secara sederhana dari level tersebut dan rasio 1R/2R.

## Sebelum dipakai untuk uang sungguhan
Tambahkan pembaruan otomatis yang terukur, pengecekan timestamp candle dan keterlambatan data, validasi spread HFM, penanganan berita berdampak tinggi, pengamanan API key, pengujian historis tanpa look-ahead bias, dan pengujian akun demo. Jangan gunakan sinyal ini sebagai satu-satunya dasar transaksi.
