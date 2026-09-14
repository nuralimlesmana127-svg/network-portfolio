# Analisis Perbandingan Performa Protokol OSPF dan IS-IS Berbasis Simulasi PNETLab

Repositori ini mendokumentasikan secara komprehensif proyek perancangan, implementasi, dan evaluasi jaringan mandiri yang dikembangkan sebagai karya independen. Seluruh arsitektur topologi, konfigurasi perangkat, hingga skenario pengujian dirancang dan dieksekusi secara mandiri untuk menguji performa protokol *Interior Gateway Protocol* (IGP) berbasis *link-state*, yaitu **OSPF (Open Shortest Path First)** dan **IS-IS (Intermediate System to Intermediate System)**.

---

## Latar Belakang & Motivasi Proyek

Dalam ekosistem jaringan telekomunikasi skala *enterprise* dan *service provider*, keandalan jalur transmisi serta kecepatan rekonvergensi saat terjadi gangguan merupakan parameter vital. Proyek ini diinisiasi untuk mengeksplorasi secara mandiri karakteristik perilaku kedua protokol utama tersebut pada topologi jaringan redundan. 

Karena dikembangkan secara independen, proyek ini memberikan keleluasaan penuh dalam memanipulasi variabel pengujian—mulai dari rekayasa *link*, injeksi kegagalan perangkat (*node failure*), hingga ekstraksi data metrik secara presisi tanpa batasan operasional jaringan produksi.

---

## Metodologi & Lingkungan Simulasi

* **Platform Emulasi:** PNETLab (*Professional Network Emulation Lab*)
* **Perangkat Jaringan:** 6 Unit Cisco Router (Menggunakan *image* `i86bi-linux-l3-jk9s-15.0.1`)
* **Perangkat Pendukung / Host:** Lenovo IdeaPad V14-ADA (AMD Athlon Gold 3150U, RAM 8 GB, SSD 512 GB)
* **Parameter Pengujian Utama:**
  1. **Latency & Jitter (Kondisi Stabil):** Pengukuran *Round-Trip Time* (RTT) rata-rata dan maksimum untuk menilai efisiensi pengiriman paket harian.
  2. **Convergence Time (Pemulihan Jalur):** Pengukuran jumlah paket ICMP yang hilang (*packet loss*) saat dilakukan *shutdown* pada jalur utama untuk menguji seberapa cepat protokol memulihkan rute alternatif.

---

## Ringkasan Hasil Analisis Komparatif

Berdasarkan eksperimen terstruktur yang telah dilakukan pada topologi mandiri, diperoleh hasil perbandingan sebagai berikut:

| Metrik Evaluasi | IS-IS | OSPF | Analisis & Implikasi Teknis |
| :--- | :---: | :---: | :--- |
| **Kecepatan Konvergensi** | **Unggul** (14.3 paket hilang) | Kalah (21.7 paket hilang) | **IS-IS** menunjukkan rekonvergensi yang lebih agresif dan cepat dalam mengalihkan trafik saat terjadi kegagalan *link*. |
| **Rata-rata Latency (Avg)** | Kalah (10.3 ms) | **Unggul** (7.7 ms) | **OSPF** menawarkan *overhead* pemrosesan jalur awal yang lebih efisien untuk penggunaan harian. |
| **Stabilitas Jalur (Jitter)** | Kalah (Max 365.0 ms) | **Unggul** (Max 132.7 ms) | **OSPF** terbukti lebih stabil dan tahan terhadap fluktuasi *delay* yang ekstrem saat transisi topologi. |

---

## Kesimpulan Proyek

* **IS-IS** sangat ideal diterapkan pada jaringan inti (*core backbone*) skala masif di mana ketersediaan tinggi (*high availability*) dan kecepatan pemulihan mutlak menjadi prioritas utama.
* **OSPF** menjadi pilihan terbaik untuk arsitektur jaringan yang menuntut kualitas layanan (*QoS*) stabil dengan tingkat *jitter* dan *delay* yang rendah.

---

## Struktur Direktori Repositori

```text
├── README.md                 # Dokumentasi utama proyek
├── topologi/                 # Berkas skema rancangan topologi PNETLab (.unl)
└── Hsil_Pengujian/           # Log mentah hasil pengujian latency dan packet loss
