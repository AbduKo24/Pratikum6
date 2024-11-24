# Pratikum 6
## NAMA:MUHAMAD ABDU
## KELAS:TI.24.A1
# NIM:312410143

## Hasil Input 
```python
data_mahasiswa = {}

def lihat_data():
    if not data_mahasiswa:
        print("Daftar Nilai")
        print("=" * 81)
        print(f"{'No'.center(5)}|{'Nama'.center(15)}|{'NIM'.center(10)}|{'Nilai Tugas'.center(13)}|{'Nilai UTS'.center(10)}|{'Nilai UAS'.center(10)}|{'Nilai Akhir'.center(10)}|")
        print("=" * 81)
        print(f"{'TIDAK ADA DATA'.center(75)}")
        print("=" * 81)
        return
    print("Daftar Nilai")
    print("=" * 81)
    print(f"{'No'.center(5)}|{'Nama'.center(15)}|{'NIM'.center(10)}|{'Nilai Tugas'.center(13)}|{'Nilai UTS'.center(10)}|{'Nilai UAS'.center(10)}|{'Nilai Akhir'.center(10)}|")
    print("=" * 81)
    for i, (nim, mhs) in enumerate(data_mahasiswa.items(), start=1):
        print(f"{str(i).center(5)}|{mhs['nama'].ljust(15)}|{nim.center(10)}|{str(mhs['tugas']).center(13)}|{str(mhs['uts']).center(10)}|{str(mhs['uas']).center(10)}|{format(mhs['nilai_akhir'], '.2f').center(10)} |")
    print("=" * 81)

def tambah_data():
    print("Tambah Data")
    nim = input("NIM: ")
    if nim in data_mahasiswa:
        print("Data dengan NIM tersebut sudah ada!")
        return
    nama = input("Nama: ")
    tugas = float(input("Nilai Tugas: "))
    uts = float(input("Nilai UTS: "))
    uas = float(input("Nilai UAS: "))
    nilai_akhir = (tugas * 0.3) + (uts * 0.35) + (uas * 0.35)

    data_mahasiswa[nim] = {
        "nama": nama,
        "tugas": tugas,
        "uts": uts,
        "uas": uas,
        "nilai_akhir": nilai_akhir
    }
    print("Data berhasil ditambahkan!")

def ubah_data():
    lihat_data()
    if not data_mahasiswa:
        return
    
    nim = input("Masukkan NIM data yang akan diubah: ")
    if nim in data_mahasiswa:
        print("Masukkan Data Baru")
        nama = input("Nama: ")
        tugas = float(input("Nilai Tugas: "))
        uts = float(input("Nilai UTS: "))
        uas = float(input("Nilai UAS: "))
        nilai_akhir = (tugas * 0.3) + (uts * 0.35) + (uas * 0.35)

        data_mahasiswa[nim] = {
            "nama": nama,
            "tugas": tugas,
            "uts": uts,
            "uas": uas,
            "nilai_akhir": nilai_akhir
        }
        print("Data berhasil diubah!")
    else:
        print("NIM tidak ditemukan!")

def hapus_data():
    lihat_data()
    if not data_mahasiswa:
        return

    nim = input("Masukkan NIM data yang akan dihapus: ")
    if nim in data_mahasiswa:
        del data_mahasiswa[nim]
        print("Data berhasil dihapus!")
    else:
        print("NIM tidak ditemukan!")

def cari_data():
    keyword = input("Masukkan nama atau NIM yang ingin dicari: ")
    hasil_cari = {nim: mhs for nim, mhs in data_mahasiswa.items() if keyword.lower() in mhs['nama'].lower() or keyword in nim}
    
    if hasil_cari:
        print("Hasil Pencarian:")
        print("=" * 81)
        print(f"{'No'.center(5)}|{'Nama'.center(15)}|{'NIM'.center(10)}|{'Nilai Tugas'.center(13)}|{'Nilai UTS'.center(10)}|{'Nilai UAS'.center(10)}|{'Nilai Akhir'.center(10)}|")
        print("=" * 81)
        for i, (nim, mhs) in enumerate(hasil_cari.items(), start=1):
            print(f"{str(i).center(5)}|{mhs['nama'].ljust(15)}|{nim.center(10)}|{str(mhs['tugas']).center(13)}|{str(mhs['uts']).center(10)}|{str(mhs['uas']).center(10)}|{format(mhs['nilai_akhir'], '.2f').center(10)}|")
        print("=" * 81)
    else:
        print("Data tidak ditemukan.")

while True:
    pilihan = input("[(L)ihat (T)ambah (U)bah (H)apus (C)ari (K)eluar] : ").lower()
    if pilihan == 't':
        tambah_data()
    elif pilihan == 'u':
        ubah_data()
    elif pilihan == 'h':
        hapus_data()
    elif pilihan == 'l':
        lihat_data()
    elif pilihan == 'c':
        cari_data()
    elif pilihan == 'k':
        print("Program selesai.")
        break
    else:
        print("Pilihan tidak valid!")

```

# Hasil Output
````markdown
[(L)ihat (T)ambah (U)bah (H)apus (C)ari (K)eluar] : t
Tambah Data
NIM: 312410143
Nama: Muhamad Abdu
Nilai Tugas: 90
Nilai UTS: 94
Nilai UAS: 96
Data berhasil ditambahkan!
[(L)ihat (T)ambah (U)bah (H)apus (C)ari (K)eluar] : l
Daftar Nilai
=================================================================================
  No |      Nama     |   NIM    | Nilai Tugas |Nilai UTS |Nilai UAS |Nilai Akhir|
=================================================================================
  1  |Muhamad Abdu   |312410143 |     90.0    |   94.0   |   96.0   |  93.50    |
=================================================================================
[(L)ihat (T)ambah (U)bah (H)apus (C)ari (K)eluar] : k
Program selesai.
````
# Flowchart
 ![Flowchart](/flowchart.png)
 # Penjelasan
Berikut adalah penjelasan mengenai program yang telah Anda berikan:

### 1. **Penjelasan Struktur Program**

Program ini berfungsi untuk mengelola data mahasiswa, termasuk data nilai tugas, UTS, dan UAS mereka. Data tersebut disimpan dalam sebuah dictionary yang disebut `data_mahasiswa`, dengan NIM sebagai kunci (key) dan nilai berupa dictionary yang berisi nama, nilai tugas, UTS, UAS, serta nilai akhir.

Program menyediakan beberapa pilihan untuk berinteraksi dengan data mahasiswa:

- **(L)ihat**: Menampilkan semua data mahasiswa yang ada.
- **(T)ambah**: Menambah data mahasiswa baru.
- **(U)bah**: Mengubah data mahasiswa yang sudah ada.
- **(H)apus**: Menghapus data mahasiswa berdasarkan NIM.
- **(C)ari**: Mencari data mahasiswa berdasarkan nama atau NIM.
- **(K)eluar**: Keluar dari program.

### 2. **Penjelasan Fungsi-fungsi dalam Program**

- **lihat_data()**:
  - Fungsi ini digunakan untuk menampilkan daftar nilai mahasiswa.
  - Jika data mahasiswa kosong, program akan menampilkan pesan "TIDAK ADA DATA".
  - Jika ada data mahasiswa, fungsi ini akan menampilkan data mahasiswa dengan format tabel yang rapi, mencakup kolom: No, Nama, NIM, Nilai Tugas, Nilai UTS, Nilai UAS, dan Nilai Akhir.
  
- **tambah_data()**:
  - Fungsi ini menambahkan data mahasiswa baru ke dalam `data_mahasiswa`.
  - Program meminta input NIM, nama, nilai tugas, nilai UTS, dan nilai UAS dari pengguna.
  - Nilai akhir dihitung berdasarkan rumus `(tugas * 0.3) + (uts * 0.35) + (uas * 0.35)`.
  - Program memeriksa apakah NIM yang dimasukkan sudah ada di dalam data; jika sudah ada, data tidak akan ditambahkan.

- **ubah_data()**:
  - Fungsi ini mengubah data mahasiswa yang sudah ada.
  - Program akan menampilkan daftar mahasiswa terlebih dahulu, lalu meminta pengguna untuk memasukkan NIM mahasiswa yang ingin diubah.
  - Jika NIM ditemukan, program meminta input data baru untuk nama, nilai tugas, UTS, dan UAS, kemudian menghitung nilai akhir dan memperbarui data tersebut.

- **hapus_data()**:
  - Fungsi ini menghapus data mahasiswa berdasarkan NIM.
  - Program akan menampilkan daftar mahasiswa, lalu meminta pengguna untuk memasukkan NIM yang ingin dihapus.
  - Jika NIM ditemukan, data mahasiswa akan dihapus dari `data_mahasiswa`.

- **cari_data()**:
  - Fungsi ini mencari data mahasiswa berdasarkan nama atau NIM.
  - Program meminta input berupa keyword, lalu mencari data mahasiswa yang nama atau NIM-nya mengandung keyword tersebut.
  - Hasil pencarian ditampilkan dalam format tabel yang sama dengan fungsi `lihat_data()`. Jika tidak ada data yang ditemukan, program akan memberikan pesan "Data tidak ditemukan".

### 3. **Penjelasan Alur Program**

Program ini bekerja dalam sebuah **loop utama** yang terus berjalan sampai pengguna memilih opsi 'K' untuk keluar. Pada setiap iterasi, program menampilkan pilihan menu dan meminta pengguna untuk memasukkan pilihan. Berdasarkan pilihan tersebut, program akan mengeksekusi fungsi yang sesuai.

Contoh alur yang dijelaskan oleh output yang Anda berikan:

1. **Tambah Data (T)**:
   - Pengguna memasukkan data mahasiswa baru (NIM, Nama, Nilai Tugas, UTS, UAS).
   - Data tersebut berhasil ditambahkan ke dalam dictionary `data_mahasiswa`.

2. **Lihat Data (L)**:
   - Setelah menambahkan data, pengguna memilih untuk melihat daftar mahasiswa.
   - Program menampilkan data mahasiswa dalam bentuk tabel yang mencakup informasi yang baru saja ditambahkan.

3. **Keluar (K)**:
   - Pengguna memilih untuk keluar dari program setelah melihat data.

### 4. **Contoh Output**

Misalnya, berikut adalah contoh output saat pengguna menjalankan program:

- **Tambah Data**:
  ```
  [(L)ihat (T)ambah (U)bah (H)apus (C)ari (K)eluar] : t
  Tambah Data
  NIM: 312410143
  Nama: Muhamad Abdu
  Nilai Tugas: 90
  Nilai UTS: 94
  Nilai UAS: 96
  Data berhasil ditambahkan!
  ```

- **Lihat Data**:
  ```
  [(L)ihat (T)ambah (U)bah (H)apus (C)ari (K)eluar] : l
  Daftar Nilai
  ===============================================================================
    No |      Nama     |   NIM    | Nilai Tugas |Nilai UTS |Nilai UAS |Nilai Akhir|
  ===============================================================================
    1  |Muhamad Abdu   |312410143 |     90.0    |   94.0   |   96.0   |  93.50    |
  ===============================================================================
  ```

- **Keluar**:
  ```
  [(L)ihat (T)ambah (U)bah (H)apus (C)ari (K)eluar] : k
  Program selesai.
  ```

### 5. **Peningkatan yang Bisa Dilakukan**

- Validasi input dapat diperbaiki, misalnya dengan memeriksa apakah input nilai berupa angka atau tidak.
- Menambahkan fungsionalitas untuk mengedit hanya sebagian data, misalnya mengubah hanya nilai tugas, UTS, atau UAS tanpa harus memasukkan ulang seluruh data.
