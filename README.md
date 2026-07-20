# Portofolio Sulistiawan

Website portofolio personal — statis (HTML/CSS/JS), tanpa perlu backend, siap deploy ke Vercel lewat GitHub.

## Struktur folder

```
├── index.html              # seluruh halaman (styling & script sudah menyatu di file ini)
└── assets/
    └── cv-sulistiawan.pdf  # file CV yang bisa diunduh pengunjung
```

## Menjalankan di komputer sendiri

Tidak perlu instalasi apa pun. Cukup buka `index.html` langsung di browser,
atau jalankan server lokal sederhana:

```bash
npx serve .
```

## Upload dari HP (paling gampang)

CV sudah **ditempel langsung di dalam `index.html`** (format base64), jadi
kamu **cukup upload 1 file** ini — tombol "Download CV" akan langsung jalan
tanpa perlu folder `assets` sama sekali:

1. Buka repo GitHub kamu lewat browser HP → **Add file → Upload files**
2. Upload cuma `index.html` (dan `cikops-demo.html` kalau mau ikut fitur demo proyek)
3. Commit

Folder `assets/` tetap ada di paket ini untuk cadangan/backup CV asli dan logo
proyek CIKOPS-FM (dipakai oleh `cikops-demo.html`) — tapi khusus untuk CV di
halaman utama, folder itu **tidak wajib** diupload.

## Upload ke GitHub (lewat command line, lebih lengkap)

```bash
git init
git add .
git commit -m "Portofolio Sulistiawan"
git branch -M main
git remote add origin https://github.com/USERNAME/NAMA-REPO.git
git push -u origin main
```

## Deploy ke Vercel

1. Buka [vercel.com](https://vercel.com) → **Add New Project**
2. Pilih repository GitHub yang baru dibuat
3. Framework preset: pilih **Other** (karena ini situs statis biasa)
4. Build command & output directory: kosongkan saja
5. Klik **Deploy** — selesai dalam hitungan detik

Setiap kali kamu `git push` perubahan baru, Vercel otomatis build ulang.

## Mengganti foto profil

Foto profil kamu **sudah ditempel langsung di dalam `index.html`** (base64,
sama seperti CV) — jadi kalau upload cuma file `index.html`, foto tetap tampil
permanen untuk semua pengunjung, di semua device.

Tombol kamera "📷" di halaman tetap ada untuk **preview cepat** (misal mau coba
foto lain) — tapi itu cuma tampil di browser kamu sendiri saat itu juga, tidak
tersimpan permanen. Untuk ganti foto secara permanen, cara termudah adalah
balik ke Claude dan minta "ganti foto profil di web ini dengan foto baru".

## Mengganti file CV

CV di halaman ini ditempel sebagai teks base64 langsung di dalam `index.html`
(bukan file terpisah), supaya bisa upload cuma 1 file dari HP. Kalau mau ganti
ke versi CV yang lebih baru, ini paling gampang dilakukan lewat Claude lagi —
tinggal upload CV baru dan minta "ganti CV yang bisa didownload di web ini".

Kalau mau melakukannya sendiri secara manual: convert PDF baru ke base64
(banyak tool online gratis untuk ini, cari "PDF to base64 converter"), lalu di
`index.html` cari dua baris yang diawali `data:application/pdf;base64,` dan
ganti teks panjang setelahnya dengan hasil base64 yang baru — dilakukan di
kedua tempat (tombol di navbar dan tombol di hero).

## Menambahkan form kontak / database (opsional, tahap lanjut)

Situs ini murni statis. Jika nanti ingin menambahkan form yang datanya
tersimpan (misalnya pesan dari pengunjung), itu perlu backend — bisa
ditambahkan dengan Supabase + Vercel Serverless Function di iterasi berikutnya.
