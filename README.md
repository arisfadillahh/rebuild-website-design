# Rebuild Website Design

Skill Codex untuk merancang ulang website berdasarkan riset bisnis, konten, dan aset situs asal. Cocok untuk konsep penawaran pembuatan website, pitch kepada calon klien, dan redesign yang siap dilanjutkan ke implementasi.

Alurnya: **riset → arah desain → desain editable → prototype interaktif → QA desktop/mobile → handoff**. Pilihan visual mengikuti bisnis yang diteliti; skill ini tidak mengunci semua proyek ke satu gaya.

Risetnya mengikuti proses Veselka: **audit situs di browser → baca cerita bisnis, kategori, detail produk/layanan, FAQ, dan kontak → cocokkan fakta → lihat dan pilih aset asli → hubungkan temuan ke keputusan desain → tulis dokumen riset sebelum desain utama**. [Panduan riset](skills/rebuild-website-design/references/research-and-direction.md) memuat urutan, kriteria kecukupan riset, dan contoh hubungan bukti–keputusan pada Veselka.

## Mulai cepat

**1. Install skill.** Salin prompt ini ke Codex:

~~~text
Pakai $skill-installer untuk memasang skill dari
https://github.com/arisfadillahh/rebuild-website-design/tree/main/skills/rebuild-website-design.
Setelah selesai, cek bahwa $rebuild-website-design bisa ditemukan.
~~~

Repo ini privat, jadi akun GitHub pada perangkat yang memasang harus memiliki akses. Skill siap dipakai pada giliran berikutnya; jika belum terdeteksi, mulai ulang Codex. [Alternatif instalasi manual dan pembaruan](#instalasi-manual-dan-pembaruan) ada di bawah.

**2. Sambungkan Penpot.** Ikuti [panduan Penpot langkah demi langkah](skills/rebuild-website-design/references/mcp-setup.md#remote-resmi): login → aktifkan MCP → salin URL → konfigurasi Codex → buka file desain → **File → MCP Server → Connect**. Panduan mencakup contoh konfigurasi dan prompt untuk memastikan canvas bisa dibaca. Ini cukup dilakukan saat setup; pada penggunaan berikutnya, buka file tujuan dan pastikan status MCP tersambung.

**3. Mulai redesign.** Gunakan contoh prompt lengkap di bagian berikut. Pemasangan skill tidak memasang MCP atau menghubungkan akun secara otomatis. Untuk alur lengkap dengan desain editable, siapkan browser automation, Penpot, serta kemampuan file/runtime; kebutuhan lain dijelaskan pada [matriks MCP](#mcp-dan-kemampuan-yang-diperlukan).

## Cara pakai

Setelah skill terpasang, panggil dengan nama teknis **$rebuild-website-design**. Nama yang tampil di daftar skill adalah **Rebuild Website Design**.

Contoh prompt lengkap:

~~~text
Pakai $rebuild-website-design untuk redesign https://contoh-bisnis.com.
Tujuannya untuk penawaran pembuatan website kepada pemilik bisnis.
Riset bisnis dan website-nya dulu. Ambil informasi, logo, dan foto hanya
dari website tersebut. Buat konsep yang cocok dengan bisnisnya, desain
Penpot desktop dan mobile yang bisa diedit, serta preview interaktif.
Sertakan alasan desain dan hal yang masih perlu diimplementasikan.
~~~

Contoh jika hanya membutuhkan prototype lokal:

~~~text
Pakai $rebuild-website-design untuk redesign https://contoh-bisnis.com.
Fokus ke homepage dan detail produk. Preview lokal saja; jangan publish.
~~~

Contoh jika hanya membutuhkan desain:

~~~text
Pakai $rebuild-website-design untuk https://contoh-bisnis.com.
Buat riset singkat, arah visual, dan desain Penpot desktop/mobile.
Belum perlu membuat website atau hosting.
~~~

Jika scope belum ditentukan, skill memulai dari halaman dan alur utama yang paling relevan untuk bisnis, lalu menyatakan batas hasilnya. Redesign homepage tidak dilaporkan sebagai implementasi seluruh toko.

## Hasil yang diharapkan

- Dokumen riset sebelum desain utama, beserta URL sumber, tanggal, temuan visual, dan pemetaan bukti ke keputusan desain.
- Konten dan aset yang dapat ditelusuri ke sumber asli.
- Desain Penpot yang bisa diedit, jika mode Penpot dipilih.
- Prototype dengan interaksi yang benar-benar bekerja, sesuai scope.
- Screenshot desktop dan mobile, serta ringkasan pemeriksaan yang dilakukan.
- Link desain, preview atau file lokal, dan batas implementasi.

Hasil pitch tidak otomatis mencakup checkout, payment gateway, inventori, akun, atau pengiriman. Fitur tersebut perlu backend serta pengujian tersendiri jika diminta.

## MCP dan kemampuan yang diperlukan

| Komponen | Kapan diperlukan | Peran |
| --- | --- | --- |
| Browser automation, misalnya Unified Computer Use / cua_repl | Riset visual dan QA website | Membuka situs, melihat layout, mengambil aset yang terlihat, menguji interaksi, screenshot, viewport mobile |
| Penpot MCP resmi | Desain Penpot yang editable | Membuat board desktop/mobile, mengunggah foto, menulis teks dan shape, mengekspor desain |
| Context Mode | Wajib bila aturan workspace mengharuskannya; dianjurkan untuk riset besar | Fetch/index halaman dan memproses data tanpa membanjiri konteks |
| Sites | Bila membuat preview melalui hosting Sites | Menyimpan versi dan memublikasikan preview sesuai akses yang diizinkan |
| GitHub MCP atau GitHub CLI | Bila hasil diminta masuk GitHub | Menyimpan source, dokumentasi, commit, atau PR |
| Filesystem/editor + runtime lokal | Implementasi prototype | Menulis HTML/CSS/JS atau mengikuti stack repo, menjalankan server dan pemeriksaan |

Untuk mengulang paket lengkap seperti proyek Veselka: siapkan **browser automation + Penpot**, kemampuan edit file/runtime, serta **Context Mode** jika diwajibkan workspace. **Sites dan GitHub bersifat opsional** sesuai tujuan distribusi.

Browser automation dan Sites dapat disediakan oleh plugin host; keduanya bukan nama paket npm universal yang boleh ditebak. Penamaan tool juga dapat berbeda antar aplikasi. Skill menemukan tool yang tersedia sebelum memakainya.

Panduan koneksi, pemilihan server Penpot, dan fallback ada di [MCP setup](skills/rebuild-website-design/references/mcp-setup.md).

## Instalasi manual dan pembaruan

Cara utama adalah prompt `$skill-installer` pada bagian [Mulai cepat](#mulai-cepat), sesuai [panduan skill resmi Codex](https://developers.openai.com/codex/skills). Jika ingin menyalin sendiri:

1. Buka repo dengan akun GitHub yang punya akses, lalu clone atau unduh ZIP dan ekstrak.
2. Salin **hanya folder `skills/rebuild-website-design`** beserta isinya ke `$CODEX_HOME/skills/`. Lokasi default Linux/macOS: `~/.codex/skills/`; Windows: `%USERPROFILE%\.codex\skills\`.
3. Pastikan `SKILL.md` langsung berada di folder `rebuild-website-design` seperti struktur berikut. Jangan menaruh seluruh repo atau menambahkan folder `skills` lagi di dalamnya.
4. Minta Codex membaca `$rebuild-website-design` dan menyebutkan tahapan risetnya tanpa menjalankan redesign. Jika belum terdeteksi, mulai ulang Codex.

~~~text
~/.codex/skills/rebuild-website-design/
  SKILL.md
  agents/openai.yaml
  references/
    mcp-setup.md
    research-and-direction.md
    deliverables-and-qa.md
~~~

Jika skill sudah terpasang, installer standar berhenti ketika folder tujuan sudah ada. Untuk memperbarui, salin prompt berikut:

~~~text
Perbarui skill lokal rebuild-website-design dari branch main repo
arisfadillahh/rebuild-website-design, path skills/rebuild-website-design.
Bandingkan versi lokal dengan repo dulu. Simpan cadangan di luar folder
skills jika ada perubahan lokal, lalu sinkronkan dan validasi skill.
Pertahankan konfigurasi MCP dan kredensial yang sudah terpasang.
~~~

Jika instalasi menyebut `Repository not found` atau `401/403`, pastikan akses repo tersedia melalui GitHub/Git yang dipakai installer. Login connector di aplikasi belum tentu menyediakan autentikasi Git pada terminal. Gunakan alur login GitHub yang tersedia, atau unduh ZIP lewat browser yang sudah login dan ikuti langkah manual. Jangan menaruh token di prompt atau repository.

Skill tidak membawa token, kredensial, akun klien, maupun konfigurasi hosting proyek tertentu. Hubungkan MCP melalui mekanisme resmi host yang digunakan. Untuk repo privat, akun yang memasang skill perlu memiliki akses GitHub.

## Struktur repo

- [SKILL.md](skills/rebuild-website-design/SKILL.md): instruksi utama untuk agent.
- [MCP setup](skills/rebuild-website-design/references/mcp-setup.md): kebutuhan tool dan koneksi.
- [Riset dan arah desain](skills/rebuild-website-design/references/research-and-direction.md): cara mengambil keputusan sesuai bisnis.
- [Deliverables dan QA](skills/rebuild-website-design/references/deliverables-and-qa.md): desain, prototype, pemeriksaan, dan handoff.
- [Metadata UI](skills/rebuild-website-design/agents/openai.yaml): nama dan prompt pemanggilan.

## Prinsip kualitas

Riset mendahului keputusan visual. Gunakan foto asli sebagai dasar jika diminta. Jangan mengarang testimoni, angka penjualan, klaim produk, diskon, stok, atau peningkatan konversi. Pisahkan fakta sumber dari interpretasi desain. Uji interaksi sebelum mengklaim hasilnya selesai.

Metode ini berasal dari workflow redesign Veselka; panduan memuat contoh hubungan temuan dan keputusan, sedangkan foto serta file desain klien tidak disertakan dalam paket skill. Gaya warna dan tipografi pada contoh tersebut bukan aturan untuk bisnis lain.
