# Simulasi Termometer (Virtual Lab Multi-Skala)

Simulasi termometer berbasis web (1 file HTML) untuk membandingkan 4 skala suhu: **Celsius, Fahrenheit, Kelvin,** dan **Reamur** secara real-time.

## Fitur
- Slider suhu rentang **-50°C s/d 100°C**
- Tampilan 4 termometer dengan indikator ketinggian (fill) yang sinkron
- Tombol preset suhu (mis. `0°C`, `37°C`, `100°C`)
- Rumus konversi ditampilkan di halaman

## Cara Menjalankan
**Opsi 1 (paling cepat):**
- Buka `index.html` langsung di browser.

**Opsi 2 (disarankan untuk menghindari isu path/asset):**
```bash
python3 -m http.server 8000
```
Lalu buka `http://localhost:8000`.

## Struktur Proyek
- `index.html` — seluruh UI + logika (HTML/CSS/JS)
- `docs/` — catatan/rencana perubahan

## Catatan Teknis
- UI memakai Tailwind via CDN.
- Ada referensi script `/_sdk/element_sdk.js` dan `/_sdk/data_sdk.js`. Jika folder `/_sdk` tidak tersedia di environment Anda, halaman tetap bisa dipakai, tetapi integrasi SDK tidak aktif.

## Pengembangan / Perubahan Umum
- Ubah teks judul & instruksi: elemen `#lab-title` dan `#instruction-text` di `index.html`.
- Ubah rentang slider: atribut `min/max` pada input `#temp-slider` dan rumus `fillPercent` di fungsi `updateTemperature`.

