# 🚀 Diddy's Lair: Simulasi Interaktif FPP Kustom

## 💡 Deskripsi Proyek

**Diddy's Lair** adalah sebuah proyek simulasi lingkungan 3D interaktif yang dibangun menggunakan **Unity**. Aplikasi ini menempatkan pemain sebagai Protagonis dalam sudut pandang orang pertama (First-Person Perspective/FPP) di dalam sebuah ruangan tertutup dan penuh misteri.

Fokus utama simulasi ini adalah memberikan **kebebasan eksplorasi** dan **interaksi mendalam** dengan objek-objek di lingkungan sekitar. Proyek ini juga berfungsi sebagai studi kasus teknis untuk implementasi *scripting* kustom, transformasi manual, penempatan prosedural, dan *shader* kustom di Unity.

## 🔑 Fitur Interaktif Utama

Proyek ini menampilkan serangkaian interaksi dan fitur unik yang dirancang untuk memenuhi persyaratan teknis tingkat lanjut:

* **🛋️ Sofa Interaktif:** Pemain dapat mendekati dan berinteraksi dengan Sofa untuk mengunci pandangan dan pergerakan, mensimulasikan aksi **duduk**.
* **📺 TV Dinamis:** TV di ruangan dapat dihidupkan/dimatikan. Saat menyala, layar TV memancarkan **cahaya emisif** dan memantulkan cahaya ke lingkungan, dikontrol melalui **shader animasi kustom**.
* **💣 Sistem Grenade Launcher:** Pemain dapat mengoperasikan Grenade Launcher yang **rotasinya dikontrol secara manual** oleh mouse. Launcher ini mampu mengeluarkan (spawn) amunisi (objek silinder) secara berulang ke dalam *scene*.
* **🍼 Botol Baby Oil:** Aset eksternal yang menerapkan transformasi **skala otomatis** untuk efek visual.
* **📦 Penempatan Prosedural:** Lingkungan mencakup penempatan objek dekorasi secara **prosedural** pada *startup* untuk menciptakan detail acak.

---

## 🔬 Implementasi Teknis & Persyaratan

Proyek ini secara ketat mematuhi persyaratan teknis tingkat lanjut Unity dengan implementasi manual:

### 1. Transformasi Manual (Tanpa Fungsi Built-in)

Semua transformasi diimplementasikan secara manual melalui *script* C# dengan pengubahan nilai `transform` secara langsung:

| Objek | Jenis Transformasi | Implementasi |
| :--- | :--- | :--- |
| **Grenade Launcher** | **Rotasi Terkontrol Pengguna** | Mengubah `transform.rotation` berdasarkan input mouse. |
| **Botol Baby Oil** | **Skala Otomatis** | Mengubah `transform.localScale` secara sinusoiodal (`AutoScale.cs`). |
| **FPC / Sofa** | **Translasi (Perpindahan)** | Pergerakan FPC dikontrol menggunakan `CharacterController.Move()`. |

### 2. Penempatan Objek & Prefab

* **Minimal 3 Prefab Berbeda:** Diimplementasikan sebagai: (1) Objek Prosedural, (2) Amunisi Silinder (Granat 40mm), dan (3) Botol Baby Oil.
* **Spawn Trigger Pengguna:** Amunisi Silinder ditempatkan (di-spawn) berulang kali ke dalam *scene* melalui aksi penembakan dari Grenade Launcher.

### 3. Shader Kustom (Minimal 3 Jenis)

Seluruh objek penting menggunakan *shader* yang dibangun secara kustom (bukan *shader* Unity *default*):

* **Shader Kustom 1 & 2:** Digunakan untuk Material Dinding/Lantai dan Sofa/Launcher (statis).
* **Shader Kustom 3 (Animasi Trigger):** Digunakan pada **Layar TV**. Parameter **Emissive** di *shader* diubah secara dinamis melalui skrip C# (`TV_Controller.cs`) saat tombol interaksi ditekan.

---

## 💻 Cara Menjalankan Proyek

1.  Clone repositori ini: `git clone https://www.andarepository.com/`
2.  Buka proyek di **Unity Editor** (Direkomendasikan versi: [Masukkan versi Unity yang Anda gunakan, mis. 2022.3 LTS]).
3.  Buka *scene* utama: **Assets/Scenes/DiddyLairScene** (atau nama *scene* utama Anda).
4.  Tekan tombol **Play** dan mulai eksplorasi.
