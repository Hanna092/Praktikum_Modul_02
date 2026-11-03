# Laporan Praktikum Modul 2 - Git

Nama  : HANNA AFIFAH
NIM   : 20250910011
Kelas : SINFC 02-2025

## Kata Pengantar
Puji syukur saya panjatkan kepada Allah SWT karena berkat rahmat-Nya laporan praktikum Modul 2 tentang Git ini akhirnya bisa saya selesaikan.

Laporan ini saya buat untuk praktikum Modul 2 pada mata kuliah Praktikum Desain Web, Program Studi Sistem Informasi, Fakultas Ilmu Komputer, Universitas Kuningan. Dosen pengampunya bapak Dede irawan, M.Kom .Lewat praktikum ini, saya belajar apa itu version control, cara membuat akun GitHub, cara memasang dan mengatur Git di laptop, serta perintah dasar seperti add, commit, branch, merge, dan push. Di dalam laporan ini saya tulis jawaban pre-test dan post-test, langkah-langkah praktikum lengkap dengan screenshot hasilnya, dan sedikit catatan dari apa yang saya pelajari.

Saya sadar laporan ini masih punya banyak kekurangan karena pengetahuan saya masih terbatas. Karena itu, kritik dan saran dari Bapak/Ibu dosen akan sangat saya terima. Terima kasih kepada bapak Dede Irawan, M.Kom.dan para asisten praktikum yang sudah membimbing saya selama praktikum dan penyusunan laporan ini. Semoga laporan ini bermanfaat dan bisa memenuhi tugas yang diberikan.

Kuningan, 3 November 2026

## A. Pre-Test
### 1. Tujuan version control
Version control adalah sistem yang mencatat setiap perubahan pada file proyek sehingga riwayat perubahannya tersimpan dan bisa dilihat kembali. Tujuan penggunaannya adalah:

- Menyimpan riwayat perubahan, yaitu siapa yang mengubah, apa yang diubah, dan kapan diubah.
Memudahkan pengembalian ke versi sebelumnya jika terjadi kesalahan atau error.
- Memungkinkan beberapa orang mengerjakan satu proyek yang sama tanpa saling menimpa pekerjaan.
- Memudahkan pengembangan fitur baru secara terpisah (menggunakan branch) tanpa mengganggu versi yang sudah berjalan.
- Menjadi cadangan (backup) proyek, terutama jika disimpan di remote repository seperti GitHub.
### 2. Perbedaan git add dan git commit
- git add adalah perintah untuk menambahkan file atau perubahan ke staging area (area persiapan). Pada tahap ini perubahan baru dipilih, belum disimpan sebagai versi.
- git commit adalah perintah untuk merekam perubahan yang ada di staging area ke dalam repository sebagai satu versi yang tersimpan, disertai pesan (-m) yang menjelaskan perubahan tersebut.
Jadi urutannya: git add dulu, baru git commit.
### 3. Cara membuat branch baru
- Branch baru dapat dibuat dengan perintah:
git branch nama-branch
- Setelah itu, pindah ke branch tersebut dengan:
git checkout nama-branch
- Kedua langkah itu bisa digabung menjadi satu perintah:
git checkout -b nama-branch

## B. Post-Test
### 1. Fungsi git merge
git merge adalah perintah untuk menggabungkan perubahan dari satu branch ke branch lain. Biasanya dipakai untuk memasukkan hasil kerja di branch fitur ke branch utama (main) setelah fitur itu selesai dan sudah dicek.
Contoh:
git checkout main
git merge fitur-biodata

Artinya: pindah ke branch main, lalu gabungkan isi branch fitur-biodata ke dalamnya.
### 2. Cara mengatasi konflik saat merge
Konflik terjadi ketika dua branch mengubah baris yang sama pada file yang sama, sehingga Git tidak bisa memilih sendiri isi mana yang dipakai.
Cara mengatasinya:
Ketik git status untuk melihat file mana yang berkonflik.
Buka file tersebut di VS Code. Akan ada tanda seperti ini:
   <<<<<<< HEAD
   isi dari branch saat ini
   =======
   isi dari branch yang digabung
   >>>>>>> nama-branch
Pilih isi yang benar (salah satu atau gabungan keduanya), lalu hapus tanda <<<<<<<, =======, dan >>>>>>>.
Simpan file, lalu ketik git add nama-file.
Ketik git commit untuk menyelesaikan merge.

Jika ingin membatalkan merge, gunakan git merge --abort.
### 3. Langkah menambahkan file baru dan commit
- Membuat file baru di VS Code lalu menyimpannya (Ctrl + S).
- Mengecek status file dengan perintah:
   git status
- File baru akan terlihat sebagai untracked.
- Memasukkan file ke staging area:
git add namafile.html
- Merekam perubahan ke repository:
   git commit -m "Menambahkan namafile.html"
- (Opsional) Mengirim ke GitHub:
   git push

## C. Latihan/Tugas
### Tugas 1: Membuat repository, commit, dan push
Saya membuat repository Git untuk menyimpan file HTML praktikum, lalu mengirimnya ke GitHub.dengan lewat tombal VS code tanpa terminal
Langkah-langkah:
- Klik ikon Source Control di panel paling kiri (gambar cabang, di bawah ikon kaca pembesar), atau tekan Ctrl + Shift + G.
- Klik tombol Initialize Repository. Semua file akan muncul dalam daftar Changes.
- Arahkan mouse ke tulisan Changes, klik ikon + (Stage All Changes). File berpindah ke Staged Changes.
- Di kotak Message, ketik pesan, misalnya: Menambahkan laporan Modul 2.
- Klik tombol Commit. Kalau muncul pertanyaan “stage all changes and commit?”, pilih Yes.
- Klik tombol Publish Branch (atau Publish to GitHub).
- Kalau diminta login, pilih Allow, lalu login dan Authorize di browser, kemudian kembali ke VS Code.
- Di bagian atas VS Code muncul pilihan. Pilih Publish to GitHub public repository, nama repository pweb1 (boleh diganti).
- Kalau muncul daftar file yang akan dipublikasikan, biarkan semuanya tercentang lalu klik OK.
- Tunggu sampai muncul notifikasi sukses, lalu klik Open on GitHub.
### Tugas 2: Workflow Git dengan branch
Langkah 1: Buka CMD di folder proyek
Buka File Explorer, masuk ke folder NIM_NamaKamu.
Klik address bar, ketik cmd, tekan Enter.
Cek posisi branch:
   git branch
Harus ada tanda * di main.
Langkah 2: Buat branch baru
git checkout -b fitur-biodata
Hasil: muncul Switched to a new branch 'fitur-biodata'.
Cek lagi dengan git branch. Sekarang tanda * pindah ke fitur-biodata.
Langkah 3: Ubah file di VS Code
Buka VS Code, lalu buka Modul_01/Latihan_01_01.html.
Tambahkan satu baris di dalam <body>, misalnya:
html
   <p>Ini fitur biodata</p>
Simpan dengan Ctrl + S. (Kalau lupa menyimpan, Git tidak melihat perubahannya.)
Pojok kiri bawah VS Code menampilkan nama branch aktif, harusnya fitur-biodata.

Langkah 4: Simpan perubahan di branch (commit)
Kembali ke CMD:
git status
git add .
git commit -m "Menambahkan teks biodata"

Langkah 5: Kembali ke main dan gabungkan (merge)
git checkout main
git merge fitur-biodata
Hasil: muncul Updating ... dan 1 file changed. 

Untuk membuktikan, buka lagi Latihan_01_01.html di VS Code. Baris <p>Ini fitur biodata</p> sekarang ada di branch main.

Langkah 6 : di push nya menggunkan tombol yang ada di vs code yaitu di source control

### Tugas 3: Menyimpan seluruh praktikum
Semua folder praktikum (Modul_02) saya kirim ke repository yang sama dengan 3 perintah di CMD:

git add . (masukkan semua file; tanda titik artinya “semua”)
git commit -m "Menambahkan seluruh praktikum" (simpan versi)
git push (kirim ke GitHub)

Setelah itu saya cek GitHub dan semua folder sudah tampil.

Kesimpulan: Semua praktikum sudah tersimpan di GitHub.
<p>Ini fitur bidata</p>
