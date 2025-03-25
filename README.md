# fuzzy

Untuk tugas Fuzzy Decision

Dibuat oleh Faiz Isai Rijal (23/517170/PA/22157)

Cara kerja program berdasarkan chatgpt.com:
1. Inisialisasi Variabel Semesta

Program mendefinisikan tiga variabel fuzzy dengan rentang nilai sebagai berikut:

    Permintaan (Demand): 1000 - 5000 unit

    Persediaan (Inventory): 100 - 600 unit

    Produksi (Production): 2000 - 7000 unit

Setiap variabel memiliki dua kategori (membership functions):

    Permintaan: "Turun" dan "Naik"

    Persediaan: "Sedikit" dan "Banyak"

    Produksi: "Berkurang" dan "Bertambah"

Fungsi keanggotaan berbentuk trapezoidal untuk masing-masing kategori.
2. Perhitungan Derajat Keanggotaan

Setelah mendefinisikan fungsi keanggotaan, program memasukkan nilai Permintaan = 4000 dan Persediaan = 300, lalu menghitung derajat keanggotaan (membership values):

    Permintaan 4000:

        "Turun" = 0.0

        "Naik" = 1.0

    Persediaan 300:

        "Sedikit" = 0.4

        "Banyak" = 0.0

Program menggunakan fungsi fuzz.interp_membership() dari scikit-fuzzy untuk menghitung keanggotaan berdasarkan nilai input.
3. Evaluasi Aturan Fuzzy

Empat aturan fuzzy diterapkan untuk menentukan produksi:

    Jika Permintaan Turun dan Persediaan Banyak, maka Produksi Berkurang.

    Jika Permintaan Turun dan Persediaan Sedikit, maka Produksi Berkurang.

    Jika Permintaan Naik dan Persediaan Banyak, maka Produksi Bertambah.

    Jika Permintaan Naik dan Persediaan Sedikit, maka Produksi Bertambah.

Untuk input saat ini (demand = 4000, inventory = 300), aturan ke-4 yang aktif:

    Min(1.0, 0.4) = 0.4 → Maka Produksi Bertambah dengan derajat 0.4.

Program menghitung aturan ini menggunakan np.fmin().
4. Agregasi Output Fuzzy

Program menggabungkan aturan-aturan yang aktif untuk membentuk keluaran fuzzy. Proses ini dilakukan dengan np.fmax() untuk mengambil nilai maksimum dari aturan yang mempengaruhi produksi.
5. Defuzzifikasi dengan Metode Centroid

Setelah mendapatkan keluaran fuzzy, program melakukan defuzzifikasi menggunakan metode centroid (fuzz.defuzz()) untuk menentukan nilai produksi dalam angka pasti. Hasilnya:

    Produksi yang disarankan: 5732.83 unit

Program juga menghitung tingkat keanggotaan hasil akhir menggunakan fuzz.interp_membership().
