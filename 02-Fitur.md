# 1. Tambah Mahasiswa
Fitur Tambah Mahasiswa digunakan untuk memasukkan data mahasiswa baru ke dalam sistem. Pengguna diminta mengisi informasi seperti NIM dan nama mahasiswa. Setelah data dimasukkan, sistem akan menyimpannya ke dalam daftar mahasiswa sehingga dapat digunakan pada proses pembayaran kas maupun pengelolaan data selanjutnya.
'''go
func tambahMahasiswa() {
	fmt.Print("Masukkan NIM : ")
	fmt.Scan(&data[n].NIM)

	fmt.Print("Masukkan Nama : ")
	fmt.Scan(&data[n].Nama)

	data[n].NominalBayar = 0
	data[n].TanggalBayar = "-"
	data[n].Tunggakan = IURAN * JUMLAH_BULAN
	data[n].Status = "Belum Lunas"

	n++

	fmt.Println("Data berhasil ditambah")
}


# 2. Ubah Mahasiswa
Fitur Ubah Mahasiswa berfungsi untuk memperbarui informasi mahasiswa yang telah tersimpan. Pengguna cukup memasukkan NIM mahasiswa yang ingin diubah, kemudian sistem akan menampilkan data yang bersangkutan sehingga informasi seperti nama dapat diperbarui sesuai kebutuhan.

# 3. Hapus Data Mahasiswa
Fitur Hapus Mahasiswa digunakan untuk menghapus data mahasiswa dari sistem. Setelah pengguna memasukkan NIM mahasiswa yang akan dihapus dan data berhasil ditemukan, sistem akan menghapus data tersebut sehingga tidak lagi muncul dalam daftar mahasiswa.

# 4. Bayar KAS
Fitur Bayar Kas digunakan untuk mencatat pembayaran kas mahasiswa. Pengguna memasukkan NIM, tanggal pembayaran, dan nominal pembayaran. Sistem kemudian akan menambahkan jumlah pembayaran ke total kas mahasiswa serta menyimpan transaksi tersebut ke dalam riwayat pembayaran.

# 5. Tampilkan Data Mahasiswa
Fitur Tampilkan Data Mahasiswa berfungsi untuk menampilkan seluruh data mahasiswa yang telah tersimpan di dalam sistem. Informasi yang ditampilkan meliputi NIM, nama mahasiswa, total pembayaran kas, tanggal pembayaran terakhir, serta status pembayaran sehingga pengguna dapat melihat kondisi pembayaran setiap mahasiswa dengan mudah.

# 6. Riwayat Pembayaran
Fitur Riwayat Pembayaran digunakan untuk menampilkan seluruh transaksi pembayaran kas yang pernah dilakukan. Informasi yang ditampilkan meliputi NIM mahasiswa, tanggal pembayaran, dan nominal pembayaran, sehingga seluruh aktivitas pembayaran dapat dilihat kembali sebagai arsip atau dokumentasi.

# 7. Keluar Program
Fitur Keluar Program digunakan untuk mengakhiri penggunaan aplikasi SIKAS. Ketika pengguna memilih menu ini, program akan menghentikan proses dan keluar dari aplikasi secara aman.
