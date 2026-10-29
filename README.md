# Proyek-1-Berpikir-Komputasional-Kelompok-10-2026
Muhammad Rakha E. Putra/16726519, Jessica Lydia Tambunan/16726119, Matahari Putra Hamid/16726044, Arsha Ismail Amarion/16726464, Aisyah Salsabila Al Jinani/16726484, Adam Hilmy Fathan Aritonang/16726414
# Deskripsi : Mengelola sistem gerbang masuk dan keluar parkir motor menggunakan KTM, plat nomor, saldo, dan status kendaraan.
 
# KAMUS :
# daftar_kartu, daftar_plat : array of string
# daftar_saldo : array of int
# daftar_status : array of bool
# i, durasi, tarif : int
# ktm_keluar, plat_keluar : string
# status_cocok : bool

# Algoritma

# Array untuk membuat slot daftar kartu, plat, saldo, dan status motor yang masuk.
# Kami menyederhanakannya dengan contoh hanya terbatas 3 slot. Untuk realnya bisa ditambah lebih banyak.

daftar_kartu = [None]*3
daftar_plat = [None]*3
daftar_saldo = [None]*3
daftar_status = [None]*3

print("==== GERBANG MASUK ====")

# Perulangan untuk memasukkan data.

for i in range(3):
    daftar_kartu[i] = input("Input KTM "+str(i+1)+" : ")
    daftar_plat[i] = input("Input plat nomor "+str(i+1)+" : ")
    daftar_saldo[i] = int(input("Input saldo awal "+str(i+1)+" : "))
    daftar_status[i] = True
    
print("Palang masuk terbuka.")
print("")

print("==== GERBANG KELUAR ====")

# Perulangan agar sistem berulang mengecek jika ada yang ingin keluar.

while True:
    ktm_keluar = input("Input KTM saat keluar (ketik selesai untuk berhenti): ")
    if ktm_keluar == "selesai":
        break
    plat_keluar = input("Input plat nomor saat keluar: ")
    status_cocok = False
    
    for i in range(3):
        if daftar_kartu[i] == ktm_keluar and daftar_plat[i] == plat_keluar and daftar_status[i] == True:
            status_cocok = True
            durasi = int(input("Input durasi parkir (jam): "))
            if durasi <= 1:
                tarif = 2000
            else:
                tarif = 2000 + ((durasi - 1) * 500)
                
            if daftar_saldo[i] >= tarif:
                daftar_saldo[i] = daftar_saldo[i] - tarif
                daftar_status[i] = False
                print("Sisa saldo:", daftar_saldo[i])
                print("Palang keluar terbuka.")
            else:
                print("Saldo tidak cukup")
                print("Palang keluar tidak terbuka.")
            break
            
    if status_cocok == False:
        print("Plat atau KTM tidak cocok. Palang terkunci.")
    print()
