# DATA2 BGA Rework — Web Dashboard (BLE)

Dashboard kontrol & monitoring BGA Rework Station lewat Bluetooth BLE, dibuka dari browser (Chrome Android), bisa di-"Add to Home Screen" jadi kayak app.

## Deploy ke GitHub Pages (gratis, sekali setup)

1. Buat repo baru di GitHub (public), misal nama `data2-bga-dashboard`.
2. Upload semua isi folder `webapp/` ini ke repo (drag-drop lewat web GitHub juga bisa, gak perlu command line):
   - `index.html`
   - `manifest.json`
   - `sw.js`
   - folder `icons/` (isinya `icon-192.png`, `icon-512.png`)
3. Di repo → **Settings** → **Pages** (menu kiri) → di bagian "Build and deployment":
   - Source: **Deploy from a branch**
   - Branch: **main**, folder **/ (root)**
   - Klik **Save**
4. Tunggu 1-2 menit, refresh halaman Settings → Pages itu — akan muncul link:
   ```
   https://<username-kamu>.github.io/data2-bga-dashboard/
   ```
5. Buka link itu di **Chrome Android** (bukan browser lain — Web Bluetooth cuma didukung Chrome/Edge/Opera berbasis Chromium).
6. Tap tombol **Connect** di app → pilih `DATA2-BGA` dari daftar device.
7. (Opsional) Buka menu Chrome (titik tiga) → **Add to Home Screen** → app-nya jadi punya icon sendiri di HP, kebuka tanpa address bar kayak app biasa.

## Update tampilan di kemudian hari

Tinggal edit file `index.html` di GitHub (bisa langsung dari web GitHub, klik ikon pensil), commit — otomatis ter-update di link yang sama, gak perlu setup ulang.

## Catatan penting

- Firmware ESP32 **wajib** sudah versi BLE (`DATA2_BGA_PIO_v3.7_BLE.zip` atau lebih baru) — versi Classic Bluetooth (`BluetoothSerial`) lama **tidak kompatibel** dengan Web Bluetooth.
- HP wajib Android + Chrome (iOS Safari **tidak mendukung** Web Bluetooth API sama sekali — keterbatasan dari Apple, bukan dari kita).
- Sekali sudah pernah dibuka & di-cache (lewat `sw.js`), app tetap bisa dibuka meski GitHub Pages down / HP lagi tanpa internet — komunikasi ke board selalu lewat Bluetooth lokal, bukan internet.
