# Desain, prototype, QA, dan handoff

Baca bagian yang sesuai dengan deliverable yang diminta.

## Desain Penpot yang bisa diedit

Gunakan file/page yang dipilih untuk tugas dan simpan identitasnya. Jika membuat baru, beri nama yang bermakna. Paket pitch biasanya terbantu oleh board desktop, mobile, dan panduan arah visual; jangan menambahkan board yang tidak memberi nilai.

Gunakan shape teks, rectangle, image fill, dan struktur bernama sesuai bagian halaman. Screenshot seluruh website dalam satu image bukan pengganti desain editable. Bentuk ulang komposisi secara semantik; font, crop, atau jarak kecil boleh berbeda jika kemampuan editor membatasi.

Baca dokumentasi member Penpot yang belum dikenal. Beberapa property ukuran/bounds bersifat read-only; gunakan operasi resize dan metode yang didokumentasikan. Pada layout terkelola, jangan memaksakan x/y seolah posisi bebas. Ikuti aturan Penpot untuk fills/strokes dan reparenting.

Gunakan ulang media dan helper yang sudah dibuat. Simpan ID penting untuk revisi. Export board lalu lihat hasilnya: teks terpotong, overlap, crop, urutan layer, dan harga/warna yang tidak konsisten perlu diperbaiki.

## Prototype yang meyakinkan

Ikuti stack repo atau pilih stack sederhana untuk scope baru. Jangan memasang framework berat hanya untuk presentasi statis.

Bangun rangkaian konten yang menjawab tugas pengunjung. Hero saja tidak cukup untuk website yang memerlukan penemuan produk, proses layanan, atau bukti pekerjaan.

Implementasikan interaksi yang relevan dengan benar:
- Pencarian: hasil cocok dan keadaan tidak ditemukan.
- Filter: isi berubah dan status terpilih terlihat.
- Detail: fakta yang konsisten dan tujuan CTA jelas.
- Favorit: status berubah, dapat dibatalkan, dan disimpan lokal bila diimplementasikan demikian.
- Menu/dialog: buka, tutup, keyboard, fokus, dan scroll bekerja.
- Form: label dan validasi masuk akal; jangan mengklaim data terkirim bila backend belum ada.
- Link eksternal: tujuan terverifikasi, tidak mengirim pesan atau transaksi secara otomatis.

Jangan menambahkan fitur hanya demi terlihat lengkap. Prototype boleh membatasi pembelian ke halaman resmi atau konsultasi jika itu sesuai brief.

## QA yang perlu dibuktikan

Pilih viewport desktop dan mobile yang mewakili penggunaan, lalu lihat hasil sebenarnya di browser. Jangan menyimpulkan responsif hanya dari adanya media query.

Periksa:
- Tidak ada overflow horizontal atau teks penting terpotong.
- Navigasi, CTA, tombol, dan urutan konten masuk akal.
- Semua gambar yang dipakai berhasil dimuat.
- Crop menjaga wajah/produk; proporsi tidak berubah karena width/height HTML dan CSS saling bertentangan.
- Harga, variasi, bahan, dan kelengkapan konsisten dengan sumber.
- Perbedaan gaya antar-Penpot dan prototype tidak mengubah pesan atau fakta.
- Jalankan alur utama yang diimplementasikan, termasuk keadaan kosong/error yang relevan.
- Dialog/menu bisa ditutup; kontrol punya label dan fokus keyboard yang terlihat.

Sebelum screenshot halaman panjang, muat bagian lazy-loaded dan pastikan gambar selesai tampil. Screenshot yang masih memuat gambar tidak menjadi bukti kualitas final.

Jalankan pemeriksaan syntax/build yang relevan dengan stack. Jangan menambah test yang sekadar menyalin implementasi atau mengulang pemeriksaan tanpa perubahan. Setelah perbaikan, ulangi bagian yang terdampak.

Bila browser atau runtime tidak tersedia, nyatakan batas verifikasi. Jangan melaporkan “sudah dites mobile” tanpa pengujian yang benar-benar dilakukan.

## Distribusi dan ketahanan preview

Untuk publikasi, ikuti skill/provider resmi dan pertahankan identitas serta audience proyek. Verifikasi status sukses; URL yang baru diperkirakan belum membuktikan deployment.

Jika preview privat meminta login, jelaskan dengan singkat. Jangan diam-diam menjadikan situs publik untuk menghilangkan gate.

Preview lokal perlu server yang masih berjalan saat dipakai. Jangan memberi URL localhost setelah menghentikan server lalu menyebutnya preview aktif. Jika server dihentikan, handoff ke preview hosted yang tersedia atau berikan cara menjalankan ulang dan file source.

Catat hasil QA dan batas implementasi pada dokumentasi proyek bila membantu penawaran. Simpan screenshot sebagai artifact; hindari menyertakan cookie, token, data akun, atau kunci dalam gambar.

## Bentuk handoff

Mulai dari hasil dan tautan. Sertakan screenshot utama yang cukup besar untuk dinilai; file screenshot seluruh halaman dapat diberikan sebagai tautan tambahan.

Jelaskan singkat:
- Halaman/alur yang selesai.
- Arah desain dan alasan bisnisnya.
- Interaksi serta viewport yang diuji.
- Data/aset sumber dan tanggal snapshot bila relevan.
- Bagian implementasi berikutnya, seperti backend, pembayaran, stok, booking, atau integrasi.

Jika upload GitHub atau satu tool terblokir, selesaikan paket lokal dan deliverable lain yang diotorisasi. Jelaskan kondisi spesifik serta langkah berikutnya tanpa mengklaim publikasi yang belum berhasil.

