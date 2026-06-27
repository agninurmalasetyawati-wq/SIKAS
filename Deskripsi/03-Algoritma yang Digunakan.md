# 1. Sequential Search
Sequential Search adalah algoritma pencarian yang dilakukan dengan memeriksa setiap elemen data secara berurutan dari awal hingga akhir sampai data yang dicari ditemukan atau seluruh data telah diperiksa. Pada program SIKAS, algoritma ini digunakan untuk menampilkan daftar mahasiswa yang memiliki status "Belum Lunas".
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

# 2. Binary Search
Binary Search adalah algoritma pencarian yang bekerja pada data yang telah diurutkan. Pada program SIKAS, data mahasiswa diurutkan terlebih dahulu berdasarkan NIM, kemudian proses pencarian dilakukan dengan membandingkan data yang dicari dengan elemen tengah hingga data ditemukan atau tidak ditemukan.
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

# 3. Selection Sort
Selection Sort adalah algoritma pengurutan yang bekerja dengan mencari elemen dengan nilai terkecil pada bagian data yang belum terurut, kemudian menukarnya dengan elemen pada posisi yang sesuai. Pada program SIKAS, algoritma ini digunakan untuk mengurutkan data mahasiswa berdasarkan nama secara ascending (A-Z).
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

# 4. Insertion Sort
Insertion Sort adalah algoritma pengurutan yang bekerja dengan menyisipkan setiap elemen ke posisi yang tepat pada bagian data yang telah terurut. Pada program SIKAS, algoritma ini digunakan untuk mengurutkan data mahasiswa berdasarkan jumlah tunggakan secara descending, sehingga mahasiswa dengan tunggakan terbesar ditampilkan terlebih dahulu.
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
