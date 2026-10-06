# Pelacak Keuangan: panduan pasang

Isi folder: `index.html` (website), `firebase-config.js` (kunci proyek), `firestore.rules` (siapa yang boleh akses).

## 1. Buat project Firebase (gratis)
1. Buka https://console.firebase.google.com, masuk dengan akun Google, klik **Create a project**. Google Analytics boleh dimatikan.
2. Menu **Build > Firestore Database > Create database**. Pilih lokasi terdekat (mis. `asia-southeast2` Jakarta), mulai dengan **production mode**.
3. Menu **Build > Authentication > Get started > Google > Enable**, isi email dukungan, simpan.
4. **Project settings (ikon roda gigi) > General > Your apps > ikon web `</>`**. Beri nama, jangan centang Hosting, klik Register. Salin nilai `apiKey`, `authDomain`, `projectId`, `appId`.

## 2. Isi konfigurasi
Buka `firebase-config.js`, ganti semua nilai `ISI_...` dengan yang disalin tadi.

## 3. Pasang aturan keamanan (jangan dilewati)
1. Buka `firestore.rules`, ganti dua email dengan email Google kamu dan temanmu.
2. Di Firebase Console: **Firestore Database > Rules**, tempel seluruh isi file itu, klik **Publish**.

Tanpa langkah ini orang lain bisa membaca dan mengubah datamu.

## 4. Taruh di internet (pilih satu)
**GitHub Pages**
1. Buat repository baru di GitHub, unggah ketiga file (`index.html`, `firebase-config.js`, `firestore.rules`).
2. **Settings > Pages > Source: Deploy from a branch > main / root > Save**.
3. Alamatnya: `https://<usernamemu>.github.io/<nama-repo>/`.

**Cloudflare Pages / Netlify**: buat akun, pilih unggah folder (drag and drop), dan alamat langsung diberikan.

## 5. Izinkan domain login
Firebase Console: **Authentication > Settings > Authorized domains > Add domain**, isi domain hasil langkah 4 (mis. `usernamemu.github.io`). Tanpa ini tombol "Masuk dengan Google" gagal.

## Cara pakai
Kamu dan temanmu membuka alamat itu, masuk dengan Google, dan catatan muncul di layar masing-masing secara realtime. Kolom "Dicatat oleh" menunjukkan siapa yang menambahkan.

## Menambah orang
Tambahkan emailnya di `firestore.rules`, lalu Publish lagi di Console.

## Catatan
- Batas paket gratis Firebase bisa berubah. Cek halaman harga resmi, tapi untuk dua sampai beberapa orang pemakaiannya jauh di bawah batas.
- Cadangan: Firestore tidak membuat cadangan otomatis di paket gratis. Ekspor data sesekali bila penting.
- Untuk mencoba di komputer sendiri, jalankan `python -m http.server` di folder ini lalu buka `http://localhost:8000`. File dengan modul tidak jalan jika dibuka langsung lewat `file://`. Tambahkan `localhost` ke Authorized domains.
