# 1. Tambah Mahasiswa
Fitur Tambah Mahasiswa digunakan untuk memasukkan data mahasiswa baru ke dalam sistem. Pengguna diminta mengisi informasi seperti NIM dan nama mahasiswa. Setelah data dimasukkan, sistem akan menyimpannya ke dalam daftar mahasiswa sehingga dapat digunakan pada proses pembayaran kas maupun pengelolaan data selanjutnya.

```go
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
```

# 2. Ubah Mahasiswa
Fitur Ubah Mahasiswa berfungsi untuk memperbarui informasi mahasiswa yang telah tersimpan. Pengguna cukup memasukkan NIM mahasiswa yang ingin diubah, kemudian sistem akan menampilkan data yang bersangkutan sehingga informasi seperti nama dapat diperbarui sesuai kebutuhan.
```go
func ubahMahasiswa() {
	var nimCari string

	fmt.Print("Masukkan NIM yang akan diubah: ")
	fmt.Scan(&nimCari)

	idx := -1

	for i := 0; i < n; i++ {
		if data[i].NIM == nimCari {
			idx = i
			break
		}
	}

	if idx != -1 {
		fmt.Print("Nama baru: ")
		fmt.Scan(&data[idx].Nama)

		fmt.Println("Data berhasil diubah")
	} else {
		fmt.Println("Data tidak ditemukan")
	}
}
```

# 3. Hapus Data Mahasiswa
Fitur Hapus Mahasiswa digunakan untuk menghapus data mahasiswa dari sistem. Setelah pengguna memasukkan NIM mahasiswa yang akan dihapus dan data berhasil ditemukan, sistem akan menghapus data tersebut sehingga tidak lagi muncul dalam daftar mahasiswa.
```go
func hapusMahasiswa() {
	var nimCari string
	idx := -1

	fmt.Print("Masukkan NIM yang akan dihapus: ")
	fmt.Scan(&nimCari)

	for i := 0; i < n; i++ {
		if data[i].NIM == nimCari {
			idx = i
			break
		}
	}

	if idx != -1 {
		for i := idx; i < n-1; i++ {
			data[i] = data[i+1]
		}

		n--

		fmt.Println("Data berhasil dihapus")
	} else {
		fmt.Println("Data tidak ditemukan")
	}
}
```

# 4. Bayar KAS
Fitur Bayar Kas digunakan untuk mencatat pembayaran kas mahasiswa. Pengguna memasukkan NIM, tanggal pembayaran, dan nominal pembayaran. Sistem kemudian akan menambahkan jumlah pembayaran ke total kas mahasiswa serta menyimpan transaksi tersebut ke dalam riwayat pembayaran.
```go
func bayarKas() {
	var nimCari string
	var bayar int

	fmt.Print("Masukkan NIM: ")
	fmt.Scan(&nimCari)

	idx := -1

	for i := 0; i < n; i++ {
		if data[i].NIM == nimCari {
			idx = i
			break
		}
	}

	if idx != -1 {

		fmt.Print("Nominal Pembayaran: ")
		fmt.Scan(&bayar)

		fmt.Print("Tanggal Pembayaran: ")
		fmt.Scan(&data[idx].TanggalBayar)

		data[idx].NominalBayar += bayar

		totalTagihan := IURAN * JUMLAH_BULAN
		data[idx].Tunggakan = totalTagihan - data[idx].NominalBayar

		if data[idx].Tunggakan <= 0 {
			data[idx].Tunggakan = 0
			data[idx].Status = "Lunas"
		} else {
			data[idx].Status = "Belum Lunas"
		}

		riwayat[nTransaksi].NIM = data[idx].NIM
		riwayat[nTransaksi].Tanggal = data[idx].TanggalBayar
		riwayat[nTransaksi].Nominal = bayar
		nTransaksi++

		fmt.Println("Pembayaran berhasil")

	} else {
		fmt.Println("Data tidak ditemukan")
	}
}
```

# 5. Tampilkan Data Mahasiswa
Fitur Tampilkan Data Mahasiswa berfungsi untuk menampilkan seluruh data mahasiswa yang telah tersimpan di dalam sistem. Informasi yang ditampilkan meliputi NIM, nama mahasiswa, total pembayaran kas, tanggal pembayaran terakhir, serta status pembayaran sehingga pengguna dapat melihat kondisi pembayaran setiap mahasiswa dengan mudah.
```go
func tampilkanData() {
	if n == 0 {
		fmt.Println("Belum ada data mahasiswa")
		return
	}

	fmt.Println("\n=== Data Mahasiswa ===")

	for i := 0; i < n; i++ {
		fmt.Println("Data ke-", i+1)
		fmt.Println("NIM             :", data[i].NIM)
		fmt.Println("Nama            :", data[i].Nama)
		fmt.Println("Nominal Bayar   :", data[i].NominalBayar)
		fmt.Println("Tanggal Bayar   :", data[i].TanggalBayar)
		fmt.Println("Tunggakan       :", data[i].Tunggakan)
		fmt.Println("Status          :", data[i].Status)
		fmt.Println("-----------------------------------------")
	}
}
```

# 6. Riwayat Pembayaran
Fitur Riwayat Pembayaran digunakan untuk menampilkan seluruh transaksi pembayaran kas yang pernah dilakukan. Informasi yang ditampilkan meliputi NIM mahasiswa, tanggal pembayaran, dan nominal pembayaran, sehingga seluruh aktivitas pembayaran dapat dilihat kembali sebagai arsip atau dokumentasi.
```go
func tampilRiwayat() {
	if nTransaksi == 0 {
		fmt.Println("Belum ada transaksi")
		return
	}

	fmt.Println("\n=== Riwayat Transaksi ===")

	for i := 0; i < nTransaksi; i++ {
		fmt.Println("Transaksi ke-", i+1)
		fmt.Println("NIM      :", riwayat[i].NIM)
		fmt.Println("Tanggal  :", riwayat[i].Tanggal)
		fmt.Println("Nominal  :", riwayat[i].Nominal)
		fmt.Println("------------------------")
	}
}
```

# 7. Keluar Program
Fitur Keluar Program digunakan untuk mengakhiri penggunaan aplikasi SIKAS. Ketika pengguna memilih menu ini, program akan menghentikan proses dan keluar dari aplikasi secara aman.
```go
	} else if pilih == 0 {
			break
```

