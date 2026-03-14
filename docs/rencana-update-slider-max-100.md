# Rencana Update: Slider Maksimum 100°C

## Tujuan
Mengubah batas maksimum slider suhu dari **150°C** menjadi **100°C**, agar konsisten dengan skala termometer (C/F/K/R) yang puncaknya sudah menampilkan nilai untuk **100°C** (mis. 212°F, 373 K, 80°R).

## Lingkup Perubahan
- File yang terdampak: `index.html`
- Komponen yang terdampak:
  - Kontrol slider (`#temp-slider`) dan label angka di bawahnya
  - Perhitungan persentase pengisian kolom termometer (fill level)

## Langkah-langkah
1. **Ubah batas slider**
   - Update atribut slider:
     - `max="150"` → `max="100"`
   - Pastikan `min` tetap `-50` dan `value` default tetap sesuai kebutuhan (saat ini `25`).

2. **Perbarui label skala di bawah slider**
   - Sesuaikan teks label kanan dari `150°C` menjadi `100°C`.
   - Sesuaikan label tengah agar representatif untuk rentang baru:
     - Opsi yang disarankan: gunakan nilai tengah rentang baru `(-50..100)` yaitu **25°C**.
     - Alternatif: gunakan **0°C** jika ingin patokan titik beku.

3. **Perbaiki perhitungan fill level termometer**
   - Saat ini komentar dan rumus mengasumsikan rentang `-50..150` (span 200).
   - Update agar sesuai rentang `-50..100` (span 150):
     - `fillPercent = clamp(((celsius + 50) / 150) * 100, 0..100)`
   - Update komentar agar tidak menyesatkan (mis. “scale from -50 to 100”).

4. **Verifikasi preset & batas input**
   - Cek tombol preset (sudah ada `100°C` maksimum) tetap valid.
   - Pastikan input slider tidak bisa melewati 100°C dan UI tetap stabil di nilai ekstrem:
     - `-50°C`, `0°C`, `25°C`, `50°C`, `100°C`.

5. **Uji cepat (manual)**
   - Geser slider ke minimum dan maksimum:
     - Pastikan tampilan angka utama, 4 skala, dan fill level sinkron.
   - Pastikan nilai puncak skala selaras:
     - `100°C` ↔ `212°F` ↔ `373 K` ↔ `80°R`.

## Kriteria Selesai (Acceptance Criteria)
- Slider hanya bergerak dalam rentang **-50°C s/d 100°C**.
- Label slider mencerminkan rentang baru (kanan menampilkan **100°C**).
- Fill level mencapai 0% di `-50°C` dan 100% di `100°C`.
- Semua konversi dan tampilan skala tetap benar pada nilai uji.

## Hasil Eksekusi
- Selesai diterapkan pada `index.html:83` (slider `max="100"` + label skala).
- Selesai diterapkan pada `index.html:248` (rumus `fillPercent` untuk rentang `-50..100`).
