# 1. Konstanta (Constant)
Konstanta digunakan untuk menyimpan nilai yang tidak berubah selama program dijalankan. Pada program SIKAS, konstanta digunakan untuk menentukan besarnya iuran kas per bulan dan jumlah bulan pembayaran.
```go
const IURAN = 10000
const JUMLAH_BULAN = 24
```
# 2. Struct
Struct digunakan untuk mengelompokkan beberapa variabel yang saling berkaitan ke dalam satu tipe data. Pada program ini terdapat struct Mahasiswa dan Transaksi.
```go
type Mahasiswa struct {
	NIM          string
	Nama         string
	NominalBayar int
	TanggalBayar string
	Tunggakan    int
	Status       string
}
```

# 3. Array
Array digunakan sebagai media penyimpanan data mahasiswa dan riwayat transaksi selama program dijalankan
```go
var data [100]Mahasiswa
var riwayat [1000]Transaksi
```

# 4. Function
Function digunakan untuk membagi program menjadi beberapa bagian sesuai dengan tugasnya sehingga kode menjadi lebih terstruktur dan mudah dipelajari.
```go
func tambahMahasiswa() {
	// proses tambah mahasiswa
}
```

# aku pengen buat kek gini lho nanti, kayak penjelasannya gitu, tapi caranya gimana
tapi kok jadinya kayak gini ya
kok kepotong

Iya, dari fotonya kelihatan penyebabnya. Kamu salah membuat code block di Markdown, jadi GitHub menganggap hanya baris pertama sebagai kode, sisanya jadi teks biasa sehingga terlihat "kepotong".

Pastikan formatnya seperti ini:

### Potongan Kode

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

Yang sering salah:

❌ Menulis ```go func tambahMahasiswa() { ...
❌ Lupa menutup dengan tiga backtick (```) di bagian bawah.
❌ Ada spasi atau karakter lain sebelum tiga backtick.

Yang benar:

Baris pertama hanya berisi:

```go
Kode dimulai di baris berikutnya.

Setelah kode selesai, tutup dengan:

```

Kalau masih kepotong, kirim isi file 02-Fitur.md atau screenshot saat mode Edit (bukan Preview). Nanti aku tunjukkan tepat bagian mana yang salah.

cara misahinnya gimana

Kalau untuk GitHub, kamu bisa membuat bagian Algoritma yang Digunakan seperti ini. Namun, ada satu catatan penting: sesuaikan dengan programmu.

✅ Sequential Search → digunakan jika programmu memang mencari data dengan memeriksa satu per satu.
✅ Selection Sort → digunakan jika programmu mengurutkan data dengan selection sort.
❌ Binary Search → hanya tulis jika benar-benar ada di kode programmu.
❌ Insertion Sort → hanya tulis jika memang dipakai untuk mengurutkan data.

Kalau dosen meminta menjelaskan keempat algoritma tersebut, meskipun programmu hanya memakai dua, kamu bisa menulis penjelasan umum seperti berikut.

⚙️ Algoritma yang Digunakan
1. Sequential Search
Penjelasan

Sequential Search adalah algoritma pencarian yang dilakukan dengan memeriksa data satu per satu mulai dari elemen pertama hingga data yang dicari ditemukan atau seluruh data selesai diperiksa. Pada program SIKAS, algoritma ini digunakan untuk mencari data mahasiswa berdasarkan NIM sebelum melakukan proses ubah data, hapus data, maupun pembayaran kas.

Contoh Kode
```go
func cariMahasiswa(nim string) int {
	for i := 0; i < n; i++ {
		if data[i].NIM == nim {
			return i
		}
	}
	return -1
}
```
2. Binary Search
Penjelasan

Binary Search adalah algoritma pencarian yang bekerja pada data yang sudah terurut. Algoritma ini membandingkan data yang dicari dengan elemen tengah, kemudian mempersempit ruang pencarian hingga data ditemukan atau tidak ditemukan.

Contoh Kode
```go
func binarySearch(nim string) int {
	left := 0
	right := n - 1

	for left <= right {
		mid := (left + right) / 2

		if data[mid].NIM == nim {
			return mid
		} else if data[mid].NIM < nim {
			left = mid + 1
		} else {
			right = mid - 1
		}
	}

	return -1
}
```
3. Selection Sort
Penjelasan

Selection Sort adalah algoritma pengurutan yang bekerja dengan mencari elemen terkecil pada bagian data yang belum terurut, kemudian menukarnya dengan elemen pada posisi yang sesuai. Proses ini diulang hingga seluruh data tersusun secara berurutan.

Contoh Kode
```go
for i := 0; i < n-1; i++ {
	min := i
	for j := i + 1; j < n; j++ {
		if data[j].Nama < data[min].Nama {
			min = j
		}
	}
	data[i], data[min] = data[min], data[i]
}
```
4. Insertion Sort
Penjelasan

Insertion Sort adalah algoritma pengurutan yang bekerja dengan menyisipkan setiap elemen ke posisi yang tepat pada bagian data yang telah terurut. Algoritma ini cocok digunakan untuk data berukuran kecil karena sederhana dan mudah diimplementasikan.

Contoh Kode
```go
for i := 1; i < n; i++ {
	key := data[i]
	j := i - 1

	for j >= 0 && data[j].Nama > key.Nama {
		data[j+1] = data[j]
		j--
	}

	data[j+1] = key
}
```
⚠️ Saran

Dari yang aku ingat, program SIKAS yang kita kerjakan menggunakan Sequential Search dan Selection Sort. Aku belum melihat ada implementasi Binary Search maupun Insertion Sort.

Kalau README GitHub ini memang untuk mendokumentasikan programmu, sebaiknya jangan mengklaim Binary Search dan Insertion Sort digunakan jika memang tidak ada di kodenya. Sebagai gantinya, kamu bisa membuat dua bagian:

Algoritma yang Digunakan
✅ Sequential Search
✅ Selection Sort
Algoritma yang Dipelajari
Binary Search
Insertion Sort

Dengan begitu dokumentasinya tetap lengkap tetapi tetap sesuai dengan isi program.

package main

import "fmt"

const IURAN = 10000
const JUMLAH_BULAN = 24

type Transaksi struct {
	NIM      string
	Tanggal  string
	Nominal  int
}

var riwayat [1000]Transaksi
var nTransaksi int

type Mahasiswa struct {
	NIM           string
	Nama          string
	NominalBayar  int
	TanggalBayar  string
	Tunggakan     int
	Status        string
}

var data [100]Mahasiswa
var n int

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

func selectionSortNamaAsc() {
	for i := 0; i < n-1; i++ {
		min := i

		for j := i + 1; j < n; j++ {
			if data[j].Nama < data[min].Nama {
				min = j
			}
		}

		data[i], data[min] = data[min], data[i]
	}

	fmt.Println("Data sudah diurutkan")
}

func insertionSortTunggakanDesc() {
	for i := 1; i < n; i++ {
		temp := data[i]
		j := i - 1

		for j >= 0 && data[j].Tunggakan < temp.Tunggakan {
			data[j+1] = data[j]
			j--
		}

		data[j+1] = temp
	}

	fmt.Println("Data sudah diurutkan")
}

func sequentialSearchBelumLunas() {
	found := false

	fmt.Println("\n=== Mahasiswa Belum Lunas ===")

	for i := 0; i < n; i++ {
		if data[i].Status == "Belum Lunas" {
			fmt.Println(data[i].NIM, "-", data[i].Nama,
				"| Tunggakan:", data[i].Tunggakan)
			found = true
		}
	}

	if !found {
		fmt.Println("Semua mahasiswa sudah lunas")
	}
}

func binarySearchNIM() {
	var nimCari string

	for i := 0; i < n-1; i++ {
		for j := 0; j < n-1-i; j++ {
			if data[j].NIM > data[j+1].NIM {
				data[j], data[j+1] = data[j+1], data[j]
			}
		}
	}

	fmt.Print("Masukkan NIM yang dicari: ")
	fmt.Scan(&nimCari)

	low := 0
	high := n - 1
	found := false

	for low <= high {
		mid := (low + high) / 2

		if data[mid].NIM == nimCari {
			fmt.Println("\nData Ditemukan")
			fmt.Println("NIM :", data[mid].NIM)
			fmt.Println("Nama :", data[mid].Nama)
			fmt.Println("Nominal Bayar :", data[mid].NominalBayar)
			fmt.Println("Tanggal Bayar :", data[mid].TanggalBayar)
			fmt.Println("Tunggakan :", data[mid].Tunggakan)
			fmt.Println("Status :", data[mid].Status)

			found = true
			break

		} else if nimCari < data[mid].NIM {
			high = mid - 1
		} else {
			low = mid + 1
		}
	}

	if !found {
		fmt.Println("Data tidak ditemukan")
	}
}

func statistik() {
	totalKas := 0
	jumlahLunas := 0

	for i := 0; i < n; i++ {
		totalKas += data[i].NominalBayar

		if data[i].Status == "Lunas" {
			jumlahLunas++
		}
	}

	fmt.Println("\n=== Statistik Kas ===")
	fmt.Println("Total Saldo Kas :", totalKas)
	fmt.Println("Jumlah Mahasiswa Lunas :", jumlahLunas)
}

func main() {
	var pilih int

	for {
		fmt.Println("\n==== Informasi Kas Mahasiswa ===")
		fmt.Println("1. Tambah Mahasiswa")
		fmt.Println("2. Ubah Data Mahasiswa")
		fmt.Println("3. Hapus Data Mahasiswa")
		fmt.Println("4. Pembayaran Kas")
		fmt.Println("5. Tampilkan Data")
		fmt.Println("6. Tampilkan Riwayat Transaksi")
		fmt.Println("7. Sequential Search (Belum Lunas)")
		fmt.Println("8. Binary Search (NIM)")
		fmt.Println("9. Selection Sort Nama")
		fmt.Println("10. Insertion Sort Tunggakan")
		fmt.Println("11. Statistik")
		fmt.Println("0. Keluar")

		fmt.Print("Pilih Menu: ")
		fmt.Scan(&pilih)

		if pilih == 1 {
			tambahMahasiswa()
		} else if pilih == 2 {
			ubahMahasiswa()
		} else if pilih == 3 {
			hapusMahasiswa()
		} else if pilih == 4 {
			bayarKas()
		} else if pilih == 5 {
			tampilkanData()
		} else if pilih == 6 {
			tampilRiwayat()
		} else if pilih == 7 {
			sequentialSearchBelumLunas()
		} else if pilih == 8 {
			binarySearchNIM()
		} else if pilih == 9 {
			selectionSortNamaAsc()
		} else if pilih == 10 {
			insertionSortTunggakanDesc()
		} else if pilih == 11 {
			statistik()
		} else if pilih == 0 {
			break
		} else {
			fmt.Println("Menu tidak tersedia")
		}
	}
}

ini code ku

Sip, sekarang aku sudah lihat keseluruhan programmu. Berarti memang programmu menggunakan keempat algoritma ini:

✅ Sequential Search
✅ Binary Search
✅ Selection Sort
✅ Insertion Sort

Jadi di GitHub kamu bisa menuliskannya seperti berikut.

⚙️ Algoritma yang Digunakan
1. Sequential Search
Penjelasan

Sequential Search adalah algoritma pencarian yang dilakukan dengan memeriksa setiap elemen data secara berurutan dari awal hingga akhir sampai data yang dicari ditemukan atau seluruh data telah diperiksa. Pada program SIKAS, algoritma ini digunakan untuk menampilkan daftar mahasiswa yang memiliki status "Belum Lunas".

Potongan Kode
```go
func sequentialSearchBelumLunas() {
	found := false

	for i := 0; i < n; i++ {
		if data[i].Status == "Belum Lunas" {
			fmt.Println(data[i].NIM, "-", data[i].Nama)
			found = true
		}
	}

	if !found {
		fmt.Println("Semua mahasiswa sudah lunas")
	}
}
```
2. Binary Search
Penjelasan

Binary Search adalah algoritma pencarian yang bekerja pada data yang telah diurutkan. Pada program SIKAS, data mahasiswa diurutkan terlebih dahulu berdasarkan NIM, kemudian proses pencarian dilakukan dengan membandingkan data yang dicari dengan elemen tengah hingga data ditemukan atau tidak ditemukan.

Potongan Kode
```go
low := 0
high := n - 1

for low <= high {
	mid := (low + high) / 2

	if data[mid].NIM == nimCari {
		fmt.Println("Data Ditemukan")
		break
	} else if nimCari < data[mid].NIM {
		high = mid - 1
	} else {
		low = mid + 1
	}
}
```
3. Selection Sort
Penjelasan

Selection Sort adalah algoritma pengurutan yang bekerja dengan mencari elemen dengan nilai terkecil pada bagian data yang belum terurut, kemudian menukarnya dengan elemen pada posisi yang sesuai. Pada program SIKAS, algoritma ini digunakan untuk mengurutkan data mahasiswa berdasarkan nama secara ascending (A-Z).

Potongan Kode
```go
for i := 0; i < n-1; i++ {
	min := i

	for j := i + 1; j < n; j++ {
		if data[j].Nama < data[min].Nama {
			min = j
		}
	}

	data[i], data[min] = data[min], data[i]
}
```
4. Insertion Sort
Penjelasan

Insertion Sort adalah algoritma pengurutan yang bekerja dengan menyisipkan setiap elemen ke posisi yang tepat pada bagian data yang telah terurut. Pada program SIKAS, algoritma ini digunakan untuk mengurutkan data mahasiswa berdasarkan jumlah tunggakan secara descending, sehingga mahasiswa dengan tunggakan terbesar ditampilkan terlebih dahulu.

Potongan Kode
```go
for i := 1; i < n; i++ {
	temp := data[i]
	j := i - 1

	for j >= 0 && data[j].Tunggakan < temp.Tunggakan {
		data[j+1] = data[j]
		j--
	}

	data[j+1] = temp
}
```
📌 Saran untuk README GitHub

Agar dokumentasi lebih rapi, urutannya bisa seperti ini:

📖 Deskripsi
🎯 Tujuan
✨ Fitur
⚙️ Algoritma yang Digunakan
   • Sequential Search
   • Binary Search
   • Selection Sort
   • Insertion Sort
💻 Cara Menjalankan Program
📷 Screenshot Output
👥 Anggota Kelompok
Sedikit masukan untuk kode binarySearchNIM()

Di fungsi binarySearchNIM(), kamu mengurutkan data NIM menggunakan Bubble Sort sebelum melakukan Binary Search:

for i := 0; i < n-1; i++ {
	for j := 0; j < n-1-i; j++ {
		if data[j].NIM > data[j+1].NIM {
			data[j], data[j+1] = data[j+1], data[j]
		}
	}
}

Artinya, selain empat algoritma di atas, programmu juga mengandung Bubble Sort pada bagian tersebut. Kalau dosen bertanya saat presentasi, kamu bisa menjelaskan bahwa:

Selection Sort digunakan untuk mengurutkan berdasarkan nama.
Insertion Sort digunakan untuk mengurutkan berdasarkan tunggakan.
Binary Search digunakan untuk mencari data berdasarkan NIM.
Sebelum Binary Search dijalankan, data NIM diurutkan terlebih dahulu menggunakan Bubble Sort, karena Binary Search membutuhkan data yang sudah terurut. Ini menunjukkan kamu memahami syarat penggunaan Binary Search.
konsep pemrograman yang diterapkan

Karena aku sudah lihat source code SIKAS-mu, berikut Konsep Pemrograman yang Diterapkan yang memang benar-benar digunakan di programmu. Ini cocok untuk dimasukkan ke README GitHub.

💻 Konsep Pemrograman yang Diterapkan

Program SIKAS (Sistem Informasi Kas Mahasiswa) menerapkan beberapa konsep dasar pemrograman dalam bahasa Go (Golang) untuk membangun sistem pengelolaan kas mahasiswa.

1. Konstanta (Constant)
Penjelasan

Konstanta digunakan untuk menyimpan nilai yang tidak berubah selama program dijalankan. Pada program SIKAS, konstanta digunakan untuk menentukan besarnya iuran kas per bulan dan jumlah bulan pembayaran.

Potongan Kode
```go
const IURAN = 10000
const JUMLAH_BULAN = 24
```
2. Struct
Penjelasan

Struct digunakan untuk mengelompokkan beberapa variabel yang saling berkaitan ke dalam satu tipe data. Pada program ini terdapat struct Mahasiswa dan Transaksi.

Potongan Kode
```go
type Mahasiswa struct {
	NIM          string
	Nama         string
	NominalBayar int
	TanggalBayar string
	Tunggakan    int
	Status       string
}
```
3. Array
Penjelasan

Array digunakan sebagai media penyimpanan data mahasiswa dan riwayat transaksi selama program dijalankan.

Potongan Kode
```go
var data [100]Mahasiswa
var riwayat [1000]Transaksi
```
4. Function
Penjelasan

Function digunakan untuk membagi program menjadi beberapa bagian sesuai dengan tugasnya sehingga kode menjadi lebih terstruktur dan mudah dipelajari.

Potongan Kode
```go
func tambahMahasiswa() {
	// proses tambah mahasiswa
}
```
# 5. Percabangan (If-Else)
Percabangan digunakan untuk menentukan tindakan berdasarkan kondisi tertentu, misalnya saat mengecek apakah data ditemukan atau apakah mahasiswa sudah lunas.
```go
if data[idx].Tunggakan <= 0 {
	data[idx].Status = "Lunas"
} else {
	data[idx].Status = "Belum Lunas"
}
```

# 6. Perulangan (Looping)
Perulangan digunakan untuk memproses data secara berulang, misalnya saat menampilkan seluruh data mahasiswa atau mencari data tertentu.
```go
for i := 0; i < n; i++ {
	fmt.Println(data[i].Nama)
}
```

# 7. Input & Output
Program menerima masukan dari pengguna menggunakan fmt.Scan() dan menampilkan informasi menggunakan fmt.Print() maupun fmt.Println().
```go
fmt.Print("Masukkan NIM : ")
fmt.Scan(&data[n].NIM)

fmt.Println("Data berhasil ditambah")
```

# 8. Operator
Program menggunakan berbagai operator seperti operator aritmatika, perbandingan, dan penugasan untuk melakukan perhitungan serta pengambilan keputusan.
```go
data[idx].NominalBayar += bayar

if data[idx].Tunggakan <= 0 {
	data[idx].Status = "Lunas"
}
```

# 9. Menu Berbasis Percabangan
Program menggunakan struktur if-else untuk menentukan menu yang dipilih pengguna dan menjalankan fungsi yang sesuai.
```go
if pilih == 1 {
	tambahMahasiswa()
} else if pilih == 2 {
	ubahMahasiswa()
} else if pilih == 3 {
	hapusMahasiswa()
}
```
