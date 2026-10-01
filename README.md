# Website PT Solo Logo Indonesia

Situs statis (Astro) dengan panel admin Decap CMS di `/admin/`.

## Coba di komputer sendiri

```
npm install
npm run dev          # website di http://localhost:4321
npm run cms          # (terminal kedua) admin lokal di http://localhost:4321/admin/
```

## Struktur konten (semua bisa diedit lewat /admin/)

| Isi | Lokasi file |
| --- | --- |
| Produk (29) | `src/content/produk/*.md` |
| Berita | `src/content/berita/*.md` |
| Lowongan | `src/content/lowongan/*.md` |
| Alamat, telepon, WhatsApp, foto hero | `src/data/site.json` |
| Foto yang diunggah lewat admin | `public/images/uploads/` |

## Online-kan (Cloudflare Pages)

1. Upload folder ini ke repo GitHub baru.
2. Cloudflare dashboard → Workers & Pages → Create → Pages → hubungkan repo.
   Build command: `npm run build`, output: `dist`.
3. Cek hasilnya di alamat `*.pages.dev`.
4. Hubungkan domain `solologoindonesia.com` (Custom domains). Kalau email domain masih dipakai,
   pastikan record MX ikut disalin.
5. Panel admin butuh login GitHub lewat OAuth. Di luar Netlify ini perlu satu worker kecil
   (misalnya `sveltia-cms-auth`). Setelah dibuat, isi `repo` dan `base_url` di `public/admin/config.yml`.

`public/_redirects` sudah memetakan alamat produk lama (WordPress) ke alamat baru supaya link lama
dan hasil Google tidak putus.

## Yang masih perlu diisi

- Data produk selain Pentacol dan Tufordi (bahan aktif, sasaran, deskripsi).
- Semua foto (lihat dokumen "Daftar Kebutuhan Gambar").
- Nomor WhatsApp sales di Pengaturan, dipakai form kontak dan tombol tanya produk.
- `public/images/og-image.jpg` (1200×630) untuk tampilan saat link dibagikan.
- Logo asli: ganti tanda "SLI" di `src/layouts/Base.astro` dan `public/favicon.svg`.
