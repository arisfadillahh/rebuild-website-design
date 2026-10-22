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

Cocok untuk mulai dengan Penpot cloud tanpa menjalankan server lokal. Langkah ini mengikuti [quick start resmi Penpot](https://help.penpot.app/mcp/#remote-mcp-in-5-steps), diperiksa 22 Oktober 2026. Instalasi skill dan koneksi MCP adalah dua langkah terpisah; memasang skill tidak otomatis menghubungkan akun Penpot.

1. Login ke [Penpot](https://design.penpot.app/) dengan akun sendiri.
2. Buka **Your account → Integrations → MCP Server**, lalu aktifkan **Status**.
3. Jika belum punya kunci, pilih pembuatan **MCP key**. Kunci hanya ditampilkan sekali; simpan secara pribadi. Jika koneksi sudah ada, gunakan URL yang tersedia tanpa membuat ulang kunci.
4. Salin **server URL** dari halaman yang sama. URL tersebut sudah menyertakan kunci sebagai `userToken`. Masukkan ke konfigurasi MCP Codex dengan nama `penpot`, mengikuti contoh di bawah.
5. Buka atau buat file desain Penpot. Di editor, pilih **File → MCP Server → Connect**. Biarkan tab ini terbuka dan halaman target tetap fokus.
6. Jalankan prompt cek koneksi di bawah dari Codex. Lanjutkan ke desain setelah tool berhasil membaca file dan halaman yang benar.

#### Konfigurasi di Codex

Jika host menyediakan formulir MCP, tambahkan server remote bernama `penpot` menggunakan server URL dari akun. Alternatif konfigurasi lokal Codex tersedia di `~/.codex/config.toml`, atau `config.toml` di folder `CODEX_HOME` jika disetel. Di Windows, lokasi default ada di `%USERPROFILE%\.codex\config.toml`.

Tambahkan bagian berikut ke file konfigurasi pribadi; ganti nilai placeholder dengan URL yang disalin dari Penpot. Jika bagian `mcp_servers.penpot` sudah ada, edit bagian itu saja, jangan membuat duplikat atau menimpa seluruh file.

~~~toml
[mcp_servers.penpot]
url = "PASTE_SERVER_URL_FROM_PENPOT_HERE"
~~~

Placeholder di atas bukan URL yang bisa dipakai. Simpan konfigurasi, lalu mulai ulang Codex jika koneksi belum dimuat. Pola `mcp_servers` dan `url` mengikuti [dokumentasi resmi konfigurasi MCP Codex](https://developers.openai.com/learn/docs-mcp#quickstart).

URL koneksi dapat berisi kunci rahasia. Masukkan melalui pengaturan atau mekanisme rahasia host; jangan simpan URL berkunci di README, repository, screenshot, log, atau contoh konfigurasi.

Membuat kunci dan mengaktifkan akses memerlukan otorisasi pengguna sesuai kebijakan host. Login dilakukan oleh pengguna jika kredensial belum tersedia. Skill tidak memberikan izin baru dengan sendirinya.

#### Cek koneksi tanpa mengubah desain

Salin prompt ini ke Codex:

~~~text
Cek koneksi MCP Penpot. Baca file dan halaman yang sedang aktif,
lalu sebutkan nama atau ID file, halaman, dan jumlah board-nya.
Jangan membuat atau mengubah desain dan jangan tampilkan token/URL berkunci.
~~~

Koneksi siap bila tool Penpot berhasil membaca file/halaman yang sesuai dengan editor. Jumlah board boleh nol pada file kosong. Terlihatnya nama server dalam konfigurasi saja belum membuktikan koneksi ke canvas bekerja. MCP bekerja pada halaman yang sedang fokus, dan hanya satu tab Penpot dapat menguasai koneksi MCP pada satu waktu.

#### Pakai Penpot untuk redesign

Buka file tujuan dan hubungkan MCP, lalu gunakan prompt berikut:

~~~text
Pakai $rebuild-website-design untuk redesign https://contoh-bisnis.com.
Riset bisnis dan situsnya dulu; gunakan informasi dan aset dari situs itu.
Di file Penpot yang sedang aktif, buat halaman baru untuk konsep ini,
berisi desain desktop dan mobile yang bisa diedit serta catatan arah desain.
Periksa hasil visualnya dan berikan link file Penpot.
Untuk sekarang fokus desain Penpot; belum perlu prototype website.
~~~

Untuk hasil lengkap seperti Veselka, ganti kalimat terakhir dengan permintaan prototype interaktif dan QA desktop/mobile. Setelah itu, gunakan file/page/board yang sama untuk revisi. Pada sesi berikutnya, buka lagi file tujuan dan periksa status koneksinya sebelum menjalankan perubahan.

### Local

Cocok bila membutuhkan kontrol operasional lokal atau konfigurasi khusus. Ikuti distribusi dan persyaratan runtime resmi saat ini. Server lokal dapat memerlukan proses server/plugin serta koneksi localhost yang diizinkan browser.

Local MCP tidak otomatis berarti data desain self-hosted: jika Penpot yang dipakai adalah cloud, file desain tetap berada di layanan cloud tersebut. Jangan menjanjikan keamanan absolut pada salah satu pilihan.

### Bila sesi terputus

Gunakan pesan error sebagai petunjuk. Jika heartbeat hilang, fokuskan tab Penpot, periksa status MCP, dan sambungkan kembali file yang benar. Jika status bertahan salah, reload editor sekali lalu periksa ulang. Jangan mengulangi mutasi sampai tahu apakah hasil sebelumnya sudah tercipta.

- **Tool Penpot belum muncul:** periksa entri MCP dan apakah URL placeholder sudah diganti; muat ulang Codex bila perlu.
- **Server tersedia tetapi canvas tidak terbaca:** buka file tujuan, gunakan **File → MCP Server → Connect**, dan pastikan tab/page yang benar sedang aktif.
- **Autentikasi gagal:** periksa status integrasi dan URL akun; jangan mencetak kunci atau membuat kunci baru sebelum memastikan penyebabnya.

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
