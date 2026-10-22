# MCP dan kemampuan host

Baca saat memeriksa kesiapan tool atau menyiapkan alur desain, implementasi, dan distribusi. Ini matriks kemampuan; nama namespace dan mekanisme koneksi dapat berubah. Temukan tool yang tersedia dan baca dokumentasi saat ini.

## Matriks kebutuhan

| Kemampuan | Status | Bukti kesiapan |
| --- | --- | --- |
| Browser automation | Diperlukan untuk audit visual dan QA | Bisa membuka situs, membaca DOM/aksesibilitas, mengambil screenshot, dan menguji viewport |
| Filesystem/editor dan runtime | Diperlukan untuk mode implementasi | Bisa menulis source, menjalankan stack proyek, dan menyajikan preview |
| Penpot MCP resmi | Diperlukan untuk deliverable Penpot | Tool bisa membaca halaman aktif; uji tulis hanya pada canvas yang dipilih untuk tugas |
| Context Mode | Diperlukan jika instruksi workspace mewajibkannya | Fetch/index/search dan eksekusi analisis tersedia |
| Sites atau provider hosting lain | Opsional untuk preview online | Site identity, audience, versi source, dan status deployment dapat diverifikasi |
| GitHub MCP atau GitHub CLI | Opsional untuk penyimpanan source | Akun dan repo tujuan teridentifikasi serta punya akses tulis |
| Image generation | Opsional jika pengguna mengizinkan aset baru | Tidak diperlukan untuk brief yang hanya memakai aset situs asal |

Tanpa Penpot, mode implementasi tetap bisa menghasilkan website; jangan mengklaim ada desain Penpot. Tanpa hosting, serahkan preview lokal/source/screenshot dan jelaskan keterbatasan. Bila deliverable yang diminta benar-benar bergantung pada kemampuan yang belum ada, minta informasi atau koneksi yang diperlukan sambil menyelesaikan pekerjaan lain.

## Browser automation

Contoh tool pada Codex desktop: mcp__cua_repl.js dari Unified Computer Use. Gunakan API browser yang didokumentasikan oleh host. Skill ini tidak menganggap Playwright, native desktop, upload, pageAssets, atau viewport override tersedia pada semua host.

Untuk situs sumber:
1. Inspeksi tampilan dan navigasi yang ada.
2. Gunakan inventaris aset halaman bila tersedia; muat area yang lazy-loaded sebelum mengambil inventaris.
3. Ambil aset terpilih, bukan semua media pada situs secara membabi buta.
4. Jangan melewati CAPTCHA atau peringatan keamanan browser. Laporkan blokir dan gunakan jalur lain yang diizinkan.

Untuk QA, gunakan kontrol browser yang disetujui. Jangan mengganti ke browser driver tersembunyi bila host membatasi otomasi.

## Penpot MCP resmi

Sumber utama: [Dokumentasi Penpot MCP](https://help.penpot.app/mcp/) dan [halaman MCP resmi](https://penpot.app/ai/mcp-server). Ikuti petunjuk versi saat ini, bukan alamat atau perintah dari contoh lama.

Tool yang digunakan dalam workflow ini:
- high_level_overview: baca sekali sesuai aturan tool.
- execute_code: baca/tulis canvas melalui API Penpot.
- penpot_api_info: cari member API yang belum diketahui.
- export_shape: lihat hasil visual board atau shape.

### Remote resmi

Cocok bila tim menggunakan Penpot cloud dan host mendukung koneksi remote. Pada setup yang dirujuk, integrasi diaktifkan melalui pengaturan akun, kunci MCP dibuat, lalu URL server resmi dimasukkan ke klien MCP. Buka file desain, aktifkan koneksi MCP untuk file tersebut, dan biarkan tab tetap aktif saat digunakan.

URL koneksi dapat berisi kunci rahasia. Masukkan melalui pengaturan atau mekanisme rahasia host; jangan simpan URL berkunci di README, repository, screenshot, log, atau contoh konfigurasi.

Membuat kunci dan mengaktifkan akses memerlukan otorisasi pengguna sesuai kebijakan host. Login dilakukan oleh pengguna jika kredensial belum tersedia. Skill tidak memberikan izin baru dengan sendirinya.

### Local

Cocok bila membutuhkan kontrol operasional lokal atau konfigurasi khusus. Ikuti distribusi dan persyaratan runtime resmi saat ini. Server lokal dapat memerlukan proses server/plugin serta koneksi localhost yang diizinkan browser.

Local MCP tidak otomatis berarti data desain self-hosted: jika Penpot yang dipakai adalah cloud, file desain tetap berada di layanan cloud tersebut. Jangan menjanjikan keamanan absolut pada salah satu pilihan.

### Bila sesi terputus

Gunakan pesan error sebagai petunjuk. Jika heartbeat hilang, fokuskan tab Penpot, periksa status MCP, dan sambungkan kembali file yang benar. Jika status bertahan salah, reload editor sekali lalu periksa ulang. Jangan mengulangi mutasi sampai tahu apakah hasil sebelumnya sudah tercipta.

Simpan ID board/shape yang dibuat, gunakan kembali pada perbaikan, dan verifikasi melalui read/export. Hindari board duplikat akibat retry.

## Context Mode

Ikuti aturan workspace jika diwajibkan. Untuk riset dan output besar, gunakan:
- ctx_fetch_and_index untuk menyimpan sumber web.
- ctx_search dengan beberapa query dalam satu panggilan.
- ctx_execute atau ctx_execute_file untuk menghitung, mencari, menyaring, dan memvalidasi data di sandbox.

Cetak hanya jawaban turunan. Tulis source dan dokumen melalui editor native yang persisten. Jangan mengandalkan filesystem sandbox analisis untuk menyimpan deliverable.

## Sites dan hosting

Sites adalah konektor/plugin host; bukan server npm universal. Jika tersedia, baca skill Sites yang terpasang untuk registrasi, identity proyek, packaging, push, versi, audience, dan deployment. Gunakan path helper dari instalasi saat ini, bukan path komputer pembuat skill.

Pertahankan project_id yang sudah ada. Jangan membuat Site lagi untuk retry yang statusnya belum jelas. Jangan menyalin manifest hosting milik klien/proyek sebelumnya.

Status deployment sukses memverifikasi publikasi. Browser gate login pada preview privat bukan berarti build gagal. Nyatakan kebutuhan login saat handoff; jangan mengubahnya menjadi publik tanpa otorisasi.

Provider lain boleh dipakai jika diminta dan tersedia. Pertahankan aturan repo serta mekanisme autentikasi resmi provider tersebut.

## GitHub

Gunakan konektor untuk memeriksa akun, repo, branch, dan akses. Jika kemampuan yang dibutuhkan tidak tersedia, GitHub CLI yang sudah terautentikasi atau browser resmi dapat menjadi fallback.

Jangan membuat repo baru ketika pengguna sudah menunjuk repo. Jika pengguna hanya meminta “masukkan ke GitHub saya”, pilih repo baru dengan nama yang relevan dan visibility privat kecuali konteks menentukan lain. Pastikan akun yang terautentikasi memang akun tujuan.

Publikasikan hanya file skill/source yang relevan. Kunci Penpot, credential hosting, secret environment, data autentikasi, dan aset klien yang tidak diminta tidak ikut dikirim.

