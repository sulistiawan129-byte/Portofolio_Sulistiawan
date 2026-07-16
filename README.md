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

## Upload ke GitHub

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

## Mengganti foto profil secara permanen

Fitur "📷" di halaman hanya menampilkan **preview di browser pengunjung sendiri**
(tidak tersimpan permanen karena situs ini statis, tanpa database). Supaya foto
tampil permanen untuk semua orang:

1. Simpan foto kamu sebagai `assets/foto-profil.jpg`
2. Di `index.html`, cari bagian:
   ```html
   <div class="avatar" id="avatar">
     <span id="avatar-initial">S</span>
     <img id="avatar-img" style="display:none;" alt="Foto Sulistiawan">
   ```
3. Ganti jadi:
   ```html
   <div class="avatar" id="avatar">
     <img src="assets/foto-profil.jpg" alt="Foto Sulistiawan">
   ```

## Mengganti file CV

Ganti file `assets/cv-sulistiawan.pdf` dengan versi terbarumu — nama file
harus tetap sama (`cv-sulistiawan.pdf`) supaya tombol "Download CV" tidak perlu diubah.
Jika ingin nama file lain, cari `cv-sulistiawan.pdf` di `index.html` dan ganti di kedua tempat.

## Menambahkan form kontak / database (opsional, tahap lanjut)

Situs ini murni statis. Jika nanti ingin menambahkan form yang datanya
tersimpan (misalnya pesan dari pengunjung), itu perlu backend — bisa
ditambahkan dengan Supabase + Vercel Serverless Function di iterasi berikutnya.
