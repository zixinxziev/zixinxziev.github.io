# AHOY's Productions — Convert Audio

Paket website statis siap deploy. Tidak memerlukan Node.js, npm, database, atau server backend.

## Isi paket

- `index.html` — halaman utama website (sudah termasuk CSS, JavaScript, animasi welcome, dan efek kursor perak).
- `_headers` — header keamanan untuk Cloudflare Pages. GitHub Pages akan mengabaikan file ini.
- `.nojekyll` — mencegah pemrosesan Jekyll pada GitHub Pages.

## Cara 1 — Deploy melalui GitHub Pages

1. Login ke [GitHub](https://github.com/).
2. Klik tombol **New repository**.
3. Isi nama repository, misalnya `ahoy-convert-audio`.
4. Pilih **Public** (atau Private jika paket/akun GitHub Anda mendukung Pages untuk repository private), lalu klik **Create repository**.
5. Di halaman repository, pilih **Add file → Upload files**.
6. Ekstrak ZIP ini di komputer, lalu upload isi foldernya. Pastikan `index.html` berada langsung di root repository, bukan di dalam subfolder tambahan.
7. Klik **Commit changes**.
8. Buka **Settings → Pages**.
9. Pada bagian **Build and deployment**, pilih **Deploy from a branch**.
10. Pilih branch **main** dan folder **/(root)**, lalu klik **Save**.
11. Tunggu proses publish selesai. Alamat website akan muncul di bagian Pages, biasanya berbentuk `https://USERNAME.github.io/ahoy-convert-audio/`.

Setiap kali Anda mengubah `index.html` dan melakukan commit/push ke branch `main`, GitHub Pages akan menerbitkan pembaruan secara otomatis.

## Cara 2 — Deploy melalui Cloudflare Pages dengan GitHub (disarankan)

1. Pastikan repository GitHub di atas sudah berisi `index.html` di root.
2. Login ke [Cloudflare Dashboard](https://dash.cloudflare.com/).
3. Pilih **Workers & Pages** dari menu.
4. Klik **Create application** atau **Create**, lalu pilih **Pages** dan opsi **Connect to Git** (nama tombol bisa sedikit berbeda mengikuti tampilan dashboard).
5. Hubungkan akun GitHub dan izinkan Cloudflare mengakses repository `ahoy-convert-audio`.
6. Pilih repository tersebut.
7. Pada pengaturan build:
   - **Production branch:** `main`
   - **Framework preset:** `None` / `No framework`
   - **Build command:** kosongkan / None
   - **Build output directory:** `.` (root repository)
8. Klik **Save and Deploy**.
9. Setelah deployment selesai, Cloudflare akan memberikan alamat seperti `https://NAMA-PROJECT.pages.dev`.
10. Buka alamat tersebut dan uji halaman Home, Converter, Bulk Convert, serta History.

Cloudflare Pages akan melakukan deployment baru otomatis setiap ada commit baru di branch produksi.

## Cara 3 — Deploy Cloudflare Pages tanpa GitHub (unggah langsung)

1. Ekstrak ZIP ini.
2. Login ke Cloudflare Dashboard → **Workers & Pages** → **Create** → **Pages**.
3. Pilih opsi **Direct Upload** / **Upload assets** jika tersedia.
4. Beri nama project, misalnya `ahoy-convert-audio`.
5. Upload isi folder deploy (file `index.html`, `_headers`, dan `.nojekyll`). Upload isi folder, bukan ZIP yang masih terkompres jika dashboard meminta file aset.
6. Klik **Deploy** dan tunggu sampai selesai.
7. Gunakan URL `https://NAMA-PROJECT.pages.dev` yang diberikan.

Catatan: metode Direct Upload praktis untuk publikasi awal, tetapi untuk pembaruan rutin Anda perlu mengunggah ulang aset. Integrasi GitHub lebih nyaman untuk update otomatis.

## Menggunakan domain sendiri (opsional)

- **Cloudflare Pages:** buka project → **Custom domains** → **Set up a custom domain**, masukkan domain milik Anda, lalu ikuti instruksi DNS yang ditampilkan Cloudflare.
- **GitHub Pages:** buka **Settings → Pages → Custom domain**, masukkan domain, simpan, lalu atur DNS domain sesuai instruksi resmi GitHub.

Jangan mengubah record DNS sebelum membaca instruksi yang ditampilkan oleh penyedia hosting/domain Anda.

## Catatan penting tentang website ini

- Konversi audio diproses di browser pengguna. File audio tidak dikirim ke server hosting oleh fitur converter ini.
- Library `lamejs` dan font Inter dipanggil dari CDN eksternal (cdnjs dan Google Fonts), sehingga koneksi internet diperlukan untuk memuatnya.
- Dukungan format seperti M4A, OGG, dan OPUS bergantung pada dukungan browser/perangkat. Pilihan yang tidak didukung akan dinonaktifkan otomatis.
- Riwayat tersimpan di `localStorage` browser/perangkat masing-masing, bukan tersinkron antarperangkat.
- GitHub Pages dan Cloudflare Pages hanya meng-host file website statis; tidak ada akun pengguna, penyimpanan cloud audio, atau backend server dalam paket ini.

## Struktur folder yang benar

```text
ahoy-convert-audio/
├── index.html
├── _headers
├── .nojekyll
└── README_DEPLOY.md
```
