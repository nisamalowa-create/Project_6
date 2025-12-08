# Project_6

GAMBAR 1
https://drive.google.com/file/d/1_enU5_jOZsNlQE_oaw4aLwEmCWfA1Ao2/view?usp=drivesdk


1. @echo off

Fungsi:
Mematikan tampilan perintah di CMD supaya output terlihat lebih rapi (hanya hasil yang tampil, bukan perintahnya).

2. echo

Contoh di gambar:

echo ==================================================
echo PEMBUAT FOLDER DAN SUBFOLDER BESERTA FILE

Fungsi:
Menampilkan teks ke layar CMD.

3. set "BASE=..."

Contoh di gambar:

set "BASE=C:\Users\PROFIT\Desktop"

Fungsi:
Menyimpan alamat folder ke dalam variabel bernama BASE supaya bisa dipakai berulang kali.

4. if not exist

Contoh:

if not exist "X:\SimulasiDrive D" (
    mkdir "X:\SimulasiDrive D"
)

Fungsi:
Mengecek apakah folder sudah ada.

Jika tidak ada, maka akan dibuat.

Jika sudah ada, dilewati.

5. mkdir

Contoh:

mkdir "%BASE%\SimulasiDrive D"

Fungsi:
Membuat folder (dan subfolder jika ditulis bersarang).

6. for /L %%A in (1,1,10) do

Perintah perulangan.

Artinya:

%%A = variabel perulangannya

(1,1,10) = dari 1 sampai 10 dengan kenaikan 1

Jadi perintah di dalam blok akan diulang 10 kali.

7. echo ... > file.txt

Contoh di gambar:

echo File A > "%BASE%\SimulasiDrive D\Folder_%%A\Subfolder A\Dokumen_%%A.txt"

Fungsi: Membuat file baru dan mengisi isinya dengan teks.

Simbol:

> → membuat file baru / menimpa file lama

>> → menambah isi file tanpa menghapus isi lama

8. Struktur yang dibuat script

Script ini akan otomatis membuat:

 Folder utama:
SimulasiDrive D
 Folder di dalamnya:

Folder_1 s/d Folder_10

 Subfolder:

Subfolder_A

Subfolder_B

 File otomatis:

Dokumen_xx.txt

Catatan_xx.txt

dll
9. Tujuan keseluruhan script

Script ini digunakan untuk: ✔ Otomatis membuat folder banyak sekaligus
✔ Membuat struktur direktori
✔ Membuat file contoh di tiap folder


GAMBAR 2
https://drive.google.com/file/d/15WLuxXnhb6v0l5oCsdrz7amwrihI-XO0/view?usp=drivesdk


1. @echo off

Fungsi: Mematikan tampilan perintah agar CMD terlihat rapi (hanya hasil yang tampil).

2. color 0c

Fungsi: Mengubah warna tampilan Command Prompt.

0 = background hitam

c = teks merah

3. set "BASE=..."

Contoh di gambar:

set "BASE=C:\Users\SERVER30\Desktop"

Fungsi: Menyimpan path dasar ke dalam variabel bernama BASE.

4. set "SOURCE=..."

Contoh:

set "SOURCE=%BASE%\SimulasiDrive_D"

Fungsi: Menentukan folder sumber data yang akan dibackup.

5. set "DEST=..."

Contoh:

set "DEST=%BASE%\SimulasiDrive_D\Daterecovery"

Fungsi: Menentukan folder tujuan hasil backup / recovery.

6. set "LOG=%DEST%\recovery_log.txt"

Fungsi: Menentukan file log untuk mencatat semua proses.

7. if not exist "%DEST%" mkdir "%DEST%"

Fungsi: Mengecek apakah folder tujuan ada.

Jika tidak ada → dibuat otomatis.

8. echo ... >> "%LOG%"

Contoh:

echo RECOVERY LOG: %date% %time% >> "%LOG%"

Fungsi: Menulis hasil aktivitas ke file log.

>> artinya menambah isi file, bukan menimpa.

9. for /r "%SOURCE%" %%f in (*.txt *.docx *.pdf) do

Fungsi: Melakukan perulangan (looping) untuk mencari file tertentu secara rekursif.

Artinya:

/r "%SOURCE%" → mencari sampai ke subfolder

%%f → variabel file

(*.txt *.docx *.pdf) → tipe file yang dicari.

10. copy "%%f" "%DEST%\" >nul

Fungsi: Menyalin file yang ditemukan ke folder tujuan.

>nul = supaya output tidak tampil.

11. echo STATUS: ... >> "%LOG%"

Fungsi: Mencatat status proses backup ke file log.

12. pause

Fungsi: Menghentikan layar CMD agar tidak langsung tertutup, menunggu pengguna tekan tombol.

13. cls

Fungsi: Membersihkan layar CMD.

Inti dari script ini:

Script ini berfungsi untuk:  Menyimulasikan data recovery / backup otomatis
 Mencari file tertentu
 Menyalin file tersebut ke folder tujuan
Mencatat aktivitas ke file log

GAMBAR 3
https://drive.google.com/file/d/1bliwqGs9URrC9SzrmuB_TjiM-0glDcaD/view?usp=drivesdk


1. @echo off

Fungsi: Mematikan tampilan perintah agar layar CMD lebih rapi.

2. set "BASE=..."

Contoh:

set "BASE=C:\Users\...\Desktop"

Fungsi: Menyimpan direktori dasar ke dalam variabel BASE.

3. set "SOURCE=%BASE%\SimulasiDrive_D"

Fungsi: Menentukan folder sumber data yang akan diproses.

4. set "DEST=%BASE%\Backup_Data"

Fungsi: Menentukan folder tujuan backup/recovery.

5. :MENU

Baris ini adalah label untuk menu.

Fungsi: Digunakan sebagai titik lompat ketika memakai perintah goto.

6. cls

Fungsi: Membersihkan layar Command Prompt.

7. echo ...

Contoh:

echo ADVANCED DATA RECOVERY SYSTEM
echo Source folder: %SOURCE%
echo Destination: %DEST%

Fungsi: Menampilkan teks dan nilai variabel ke layar.

8. Menu pilihan (echo opsi)

Contoh di gambar:

echo 1. SELECTIVE BACKUP (Pilih Folder)
echo 2. INCREMENTAL BACKUP (Hanya File Baru/Berubah)
echo 3. EMAIL NOTIFICATION (Notifikasi Email)
echo 4. EXIT

Fungsi: Menampilkan pilihan menu ke user.
ops
9. set /p opsi=Masukan Pilihan (1-4):

Fungsi: Menerima input dari pengguna dan menyimpannya ke variabel opsi.

10. if "%opsi%"=="1" goto SELECTIVE

Fungsi: Percabangan logika:

Jika user ketik 1, lompat ke label :SELECTIVE.

11. if "%opsi%"=="2" goto INCREMENTAL

Fungsi: Jika memilih opsi 2 → lompat ke proses backup incremental.

12. if "%opsi%"=="3" goto EMAIL

Fungsi: Jika memilih opsi 3 → jalankan bagian notifikasi email.

13. if "%opsi%"=="4" goto EXIT

Fungsi: Keluar dari program.

Intinya:

Script ini berfungsi untuk: 

Menampilkan menu interaktif di CMD
 Mengatur jenis backup/recovery
 Memberi opsi pilihan ke user
 Menjalankan proses sesuai pilihan

GAMBAR 4
https://drive.google.com/file/d/1tFER0_pl8rr7sL4Pc52aJ0s9otlF1cPs/view?usp=drivesdk


1. Tampilan Program

Di CMD terlihat judul:

ADVANCED DATA RECOVERY SYSTEM

Ini adalah judul program batch yang sedang dijalankan.

2. Informasi Folder

Baris:

Source Folder : C:\Users\SERVER\Desktop\SimulasiDrive_D
Destination   : C:\Users\SERVER\Desktop\SimulasiDrive_C

Artinya:

Source Folder → folder sumber file yang akan dibackup / di-recovery

Destination → folder tujuan hasil backup

Ini berasal dari perintah:

echo Source Folder: %SOURCE%
echo Destination  : %DEST%

3. Menu Pilihan

Yang tampil di layar:

1. Selective Backup (Pilih folder)
2. Incremental Backup (Hanya file baru/berubah)
3. Email Notification (Notifikasi Email)
4. Exit

Ini dibuat dengan perintah echo.

4. Input user

Bagian:

Masukkan pilihan (1-4):

Berasal dari perintah:

set /p pilihan=Masukkan pilihan (1-4):

Fungsinya → menerima input dari keyboard.

5. Proses percabangan

Di dalam script (yang tidak terlihat tapi berjalan):

Biasanya pakai:

if "%pilihan%"=="1" goto SELECTIVE
if "%pilihan%"=="2" goto INCREMENTAL
if "%pilihan%"=="3" goto EMAIL
if "%pilihan%"=="4" goto EXIT

Fungsinya: Menjalankan bagian program sesuai pilihan user.

Kesimpulan singkat

Di layar itu sedang berjalan program .bat yang:  Menampilkan info folder
 Menampilkan menu
 Menunggu input user
 Menentukan proses backup/recovery
