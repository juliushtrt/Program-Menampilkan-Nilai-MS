# Program-Menampilkan-Nilai-MS
#### Nama    : Julius Hutabarat
#### NIM     : 312410429
#### Kelas   : TI.24.A3

# Deskripsi
Program yang dibuat bertujuan untuk mengelola data mahasiswa beserta nilai mereka. Program ini berbasis terminal dan menggunakan Python dengan fungsi-fungsi untuk menambah, menghapus, memperbarui, dan menampilkan daftar nilai mahasiswa.

# Kode Program
#Inisialisasi daftar mahasiswa
students = []

#Fungsi untuk menambah data mahasiswa
def tambah():
    nama = input("Masukan nama mahasiswa: ")
    try:
        nilai = float(input("Masukan nilai mahasiswa: "))
        students.append({"nama": nama, "nilai": nilai})
        print(f"Data Mahasiswa {nama} berhasil ditambahkan.\n")
    except ValueError:
        print("Nilai harus berupa angka.\n")

#Fungsi untuk menampilkan data
def tampilkan():
    if not students:
        print("Belum ada data mahasiswa.\n")
        return
    print("Daftar Nilai Mahasiswa:")
    print("-" * 40)
    print(f"{'Nama':<20}{'Nilai':<10}")
    print("-" * 40)
    for student in students:
        print(f"{student['nama']:<20}{student['nilai']:<10.2f}")
    print("-" * 40 + "\n")

#Fungsi untuk menghapus data
def hapus(nama):
    for student in students:
        if student['nama'].lower() == nama.lower():
            students.remove(student)
            print(f"Data mahasiswa {nama} berhasil dihapus.\n")
            return
    print(f"Data mahasiswa dengan nama '{nama}' tidak ditemukan.\n")

#Fungsi untuk mengubah data
def ubah(nama):
    for student in students:
        if student['nama'].lower() == nama.lower():
            try:
                nilai_baru = float(input(f"Masukan nilai baru untuk {nama}: "))
                student['nilai'] = nilai_baru
                print(f"Data mahasiswa {nama} berhasil diubah.\n")
                return
            except ValueError:
                print("Nilai harus berupa angka.\n")
                return
    print(f"Data mahasiswa dengan nama '{nama}' tidak ditemukan.\n")

#Menu utama
def menu():
    while True:
        print("Menu:")
        print("1. Tambah Data")
        print("2. Tampilkan Data")
        print("3. Hapus Data")
        print("4. Ubah Data")
        print("5. Keluar")
        pilihan = input("Pilih menu (1-5): ")
        print()

        if pilihan == "1":
            tambah()
        elif pilihan == "2":
            tampilkan()
        elif pilihan == "3":
            nama = input("Masukan nama mahasiswa yang akan dihapus: ")
            hapus(nama)
        elif pilihan == "4":
            nama = input("Masukan nama mahasiswa yang akan diubah: ")
            ubah(nama)
        elif pilihan == "5":
            print("Keluar dari program. Terima kasih!")
            break
        else:
            print("Pilihan tidak valid. Silakan coba lagi.\n")

#Jalankan menu utama
menu()
