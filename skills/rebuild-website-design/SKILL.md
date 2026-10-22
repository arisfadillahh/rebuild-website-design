---
name: rebuild-website-design
description: Redesign an existing business website from source research and brand assets into a business-appropriate visual direction, editable Penpot designs, and a responsive interactive prototype for client proposals or implementation. Use for website redesign or rebuild briefs; preserve requests limited to research, design, code, or local preview.
---

# Rebuild Website Design

Ubah situs asal menjadi konsep redesign yang meyakinkan untuk bisnisnya. Utamakan ketepatan konten, arah visual yang beralasan, dan hasil yang dapat ditinjau. Samakan bahasa komunikasi dengan pengguna.

## Tentukan hasil dan kemampuan

1. Baca permintaan, konteks proyek, dan instruksi repo. Temukan tool yang tersedia sebelum menyatakan suatu MCP bisa digunakan. Baca [MCP setup](references/mcp-setup.md) ketika perlu memilih kemampuan atau menyambungkan Penpot/hosting.
2. Pertahankan scope yang diminta: riset saja, desain saja, prototype, atau implementasi. Untuk penawaran website yang terbuka, pilih halaman utama dan alur terpenting untuk bisnis, lalu nyatakan scope tersebut. Jangan menyamakan prototype homepage dengan rebuild seluruh sistem.
3. Jika source repo sudah tersedia, ikuti stack dan struktur yang sesuai. Jika belum, pilih implementasi paling sederhana yang memenuhi interaksi; HTML/CSS/JS tanpa build cocok untuk presentasi yang tidak memerlukan backend.
4. Mulai dengan informasi yang tersedia. Tanyakan hanya informasi yang memengaruhi scope atau akses dan tidak bisa diperoleh dari sumber. Lanjutkan riset dan pekerjaan independen sambil menunggu.

## Riset sebelum desain

Baca [Riset dan arah desain](references/research-and-direction.md) sebelum menentukan struktur dan visual.

- Teliti situs asal: homepage, cerita bisnis, produk/layanan, harga yang relevan, FAQ, kontak, dan CTA.
- Lihat situs di browser. Ekstraksi teks saja tidak menjelaskan kualitas foto, hierarki, kepadatan, atau masalah mobile.
- Simpan sumber dan tanggal pengecekan. Bedakan fakta situs, masalah yang diamati, interpretasi desain, dan hipotesis dampak bisnis.
- Jika pengguna membatasi sumber, patuhi pembatasan itu. “Semua info dan aset dari situs ini” berarti jangan menambah foto stok, logo buatan, data pesaing, atau klaim dari luar situs.
- Bila sumber luar diizinkan dan riset tambahan diperlukan, cari rujukan yang relevan untuk pola penggunaan atau kategori bisnis. Catat sumbernya; jangan mengganti identitas brand dengan tampilan pesaing.
- Bentuk inventaris aset terpilih: URL halaman, URL aset, nama lokal, fungsi, ukuran, dan kepemilikan. Ambil resolusi yang layak dan periksa fotonya sebelum dipakai.

## Rumuskan arah visual yang cocok

Tulis brief singkat: bisnis dan tawaran utamanya, tindakan pengunjung yang dituju, kekuatan brand, hambatan pada situs sekarang, prinsip visual, dan alur konten.

Pilih warna, tipografi, kepadatan, komposisi, dan interaksi berdasarkan temuan. Jangan menerapkan “luxury editorial” pada semua bisnis. Pertahankan identitas yang dikenali, gunakan ruang dan foto secara sengaja, dan buat CTA sesuai tindakan yang masuk akal bagi pengunjung.

Jangan mengarang ulasan, klien, statistik, sertifikasi, stok, promo, atau janji hasil. Klaim seperti “meningkatkan konversi” merupakan hipotesis kecuali ada pengukuran yang mendukung.

## Buat hasil yang bisa ditinjau

Baca bagian yang relevan pada [Deliverables dan QA](references/deliverables-and-qa.md).

- Jika Penpot dipilih, buat board desktop/mobile dengan teks, shape, dan image fill yang dapat diedit. Tambahkan panduan visual ringkas bila berguna untuk pitch. Gunakan foto dan fakta sumber yang sama pada desain dan prototype.
- Jika website dipilih, implementasikan halaman dan interaksi sesuai brief: navigasi, filter, pencarian, detail produk/layanan, FAQ, atau favorit hanya jika relevan. Tautkan tindakan eksternal ke tujuan sumber yang terverifikasi.
- Perubahan susunan kecil antarmedia boleh mengikuti kebutuhan masing-masing viewport; pesan, fakta, CTA, dan arah visual harus konsisten.
- Gunakan direktori proyek terpisah atau checkout yang telah dipilih. Jangan menyalin token, identitas hosting proyek lain, maupun aset klien ke paket skill.
- Untuk prototype tanpa backend, jelaskan batasnya di titik keputusan yang relevan. Jangan membuat status sukses pesanan, pembayaran, atau pengiriman palsu.

## Periksa, distribusikan, dan serahkan

Uji di browser pada desktop dan mobile sebelum melaporkan QA lulus. Periksa foto, proporsi, pemotongan gambar, teks, overflow, interaksi utama, serta dialog/menu. Tinjau juga export Penpot, bukan hanya keberhasilan pemanggilan tool.

Perbaiki masalah yang ditemukan, lalu ulangi pemeriksaan yang terpengaruh. Jika kemampuan QA tidak tersedia, laporkan bagian yang belum diverifikasi dan serahkan hasil lain yang sudah selesai.

Untuk hosting, gunakan workflow resmi provider atau skill hosting yang tersedia. Ikuti permintaan lokal saja atau jangan publish. Gunakan preview privat untuk konsep bila sesuai dengan otorisasi dan kemampuan host; pastikan hasil deployment benar-benar sukses. Nyatakan bila preview memerlukan login. Perubahan audience menjadi publik memerlukan otorisasi pengguna.

Simpan source ke GitHub hanya ketika diminta atau sudah diotorisasi. Pilih repo yang tepat, jaga kredensial di luar source, dan periksa hasil commit/push. Repo baru dipilih privat bila pengguna tidak menentukan audience. Jangan menulis ke repo tidak terkait hanya agar upload dianggap selesai.

Handoff harus singkat dan berisi:
- Apa yang selesai dan scope-nya.
- Link Penpot, preview atau file lokal, serta ringkasan riset.
- Screenshot yang mewakili hasil.
- Pemeriksaan yang dilakukan dan batas implementasi yang masih material.

Jangan mengakhiri tugas pada rencana, screenshot kosong, atau klaim “tersambung” tanpa hasil yang dapat diperiksa.

