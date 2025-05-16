# BMI Calculator - Aplikasi Hybrid dengan Dcoder

![BMI Calculator](https://via.placeholder.com/800x400?text=BMI+Calculator+App)

## Deskripsi Proyek

BMI Calculator adalah aplikasi hybrid yang dikembangkan menggunakan Dcoder di Android. Aplikasi ini memungkinkan pengguna untuk menghitung Body Mass Index (BMI) mereka, mendapatkan rekomendasi kesehatan berdasarkan hasil BMI, dan menyimpan riwayat perhitungan.

Proyek ini memadukan elemen pengembangan web (HTML, CSS, dan JavaScript) dengan kemampuan penyimpanan lokal dan fitur perangkat untuk menciptakan pengalaman aplikasi yang menyerupai aplikasi native.

## Fitur Aplikasi

- Perhitungan BMI berdasarkan tinggi dan berat badan
- Klasifikasi BMI (Kekurangan Berat Badan, Normal, Kelebihan Berat Badan, Obesitas)
- Rekomendasi kesehatan berdasarkan kategori BMI
- Penyimpanan riwayat perhitungan BMI menggunakan localStorage
- Haptic feedback (getaran) saat menghitung hasil atau menghapus riwayat
- Antarmuka pengguna responsif dan intuitif
- Dukungan untuk jenis kelamin (Laki-laki/Perempuan)
- Tampilan visual klasifikasi BMI dengan kode warna

## Teknologi yang Digunakan

- **HTML5**: Struktur dasar aplikasi
- **CSS3**: Styling dan animasi
- **JavaScript**: Logika aplikasi dan manipulasi DOM
- **localStorage API**: Penyimpanan lokal untuk riwayat BMI
- **Vibration API**: Efek getaran untuk interaksi pengguna

## Screenshoot Aplikasi

### Halaman Utama
![Halaman Utama](https://via.placeholder.com/300x600?text=Halaman+Utama)

### Hasil Perhitungan
![Hasil Perhitungan](https://via.placeholder.com/300x600?text=Hasil+Perhitungan)

### Riwayat Perhitungan
![Riwayat Perhitungan](https://via.placeholder.com/300x600?text=Riwayat+Perhitungan)

## Struktur Proyek

```
BMI-Calculator/
│
├── index.html          # Struktur utama aplikasi
├── style.css           # Styling aplikasi
├── script.js           # Logika aplikasi
└── README.md           # Dokumentasi proyek
```

## Instalasi dan Penggunaan

### Metode 1: Penggunaan dengan Dcoder

1. Unduh dan instal aplikasi Dcoder dari Google Play Store
2. Buat proyek baru dengan tipe "Web"
3. Salin kode dari file `index.html`, `style.css`, dan `script.js` ke file yang sesuai di Dcoder
4. Jalankan aplikasi dari dalam Dcoder

### Metode 2: Penggunaan di Browser

1. Clone repositori ini:
   ```
   git clone https://github.com/Nicholas786/BMI-Calculator.git
   ```
2. Buka file `index.html` di browser apa pun

### Metode 3: Hosting sebagai Web App

1. Unggah file-file proyek ke layanan hosting web
2. Akses melalui URL yang disediakan

## Fitur Hybrid

Aplikasi ini menunjukkan konsep hybrid melalui:

1. **Pengembangan berbasis Web**:
   - Menggunakan HTML/CSS/JavaScript standar
   - Layout responsif untuk berbagai ukuran layar
   - Desain modern dengan CSS gradien dan animasi

2. **Fitur "Native-like"**:
   - Penyimpanan data lokal menggunakan localStorage API
   - Haptic feedback (getaran) menggunakan Vibration API
   - Pengalaman pengguna yang mulus dengan animasi dan transisi

## Implementasi Kode

### Perhitungan BMI

```javascript
// Fungsi perhitungan BMI
function calculateBMI(weight, height) {
    // Konversi cm ke m dan hitung BMI
    const heightInMeters = height / 100;
    return (weight / (heightInMeters * heightInMeters)).toFixed(1);
}

// Fungsi menentukan kategori BMI
function getBMICategory(bmi) {
    bmi = parseFloat(bmi);
    
    if (bmi < 18.5) {
        return 'Kekurangan Berat Badan';
    } else if (bmi >= 18.5 && bmi < 25) {
        return 'Normal (Ideal)';
    } else if (bmi >= 25 && bmi < 30) {
        return 'Kelebihan Berat Badan';
    } else {
        return 'Obesitas';
    }
}
```

### Penyimpanan Lokal

```javascript
// Menyimpan ke riwayat
function saveToHistory(name, height, weight, gender, bmi, category) {
    // Membuat objek data riwayat baru
    const now = new Date();
    const historyItem = {
        id: Date.now(), // ID unik berdasarkan timestamp
        name: name,
        height: height,
        weight: weight,
        gender: gender,
        bmi: bmi,
        category: category,
        date: now.toLocaleDateString('id-ID'),
        time: now.toLocaleTimeString('id-ID')
    };
    
    // Menambahkan ke array riwayat
    history.unshift(historyItem); // Tambahkan di awal array
    
    // Batasi jumlah riwayat yang disimpan (opsional)
    if (history.length > 10) {
        history = history.slice(0, 10);
    }
    
    // Menyimpan ke localStorage
    localStorage.setItem('bmiHistory', JSON.stringify(history));
    
    // Memperbarui tampilan riwayat
    displayHistory();
}
```

### Haptic Feedback

```javascript
// Mengatur efek haptic/getaran (simulasi sentuhan native)
if ('vibrate' in navigator) {
    navigator.vibrate(100); // Getaran 100ms
}
```

## Keunggulan Aplikasi Hybrid

1. **Pengembangan Efisien**:
   - Menggunakan teknologi web standar yang mudah dipelajari
   - Tidak memerlukan bahasa pemrograman khusus seperti Java/Kotlin

2. **Ukuran Aplikasi Kecil**:
   - File HTML, CSS, dan JavaScript memiliki ukuran total yang jauh lebih kecil dibandingkan aplikasi native

3. **Potensi Cross-Platform**:
   - Kode dapat dengan mudah digunakan kembali untuk platform lain (iOS, desktop)
   - Dapat dikonversi menjadi aplikasi berbasis PWA (Progressive Web App)

4. **Pengembangan Cepat**:
   - Iterasi dan pengujian dapat dilakukan dengan cepat
   - Tidak memerlukan kompilasi untuk setiap perubahan

## Keterbatasan dan Pengembangan Masa Depan

### Keterbatasan

- Aplikasi tidak dapat mengakses semua API perangkat yang tersedia untuk aplikasi native
- Kinerja mungkin tidak seoptimal aplikasi native untuk operasi intensif
- Pengalaman offline terbatas pada kemampuan localStorage

### Rencana Pengembangan Masa Depan

1. **Peningkatan Fitur**:
   - Grafik perkembangan BMI dari waktu ke waktu
   - Pengingat untuk pemeriksaan BMI rutin
   - Sinkronisasi data antar perangkat

2. **Peningkatan Teknologi**:
   - Konversi ke PWA (Progressive Web App) untuk pengalaman offline yang lebih baik
   - Penggunaan IndexedDB untuk penyimpanan data yang lebih canggih
   - Implementasi Service Worker untuk kemampuan offline penuh

3. **Packaging**:
   - Mengubah aplikasi web menjadi APK menggunakan Apache Cordova atau Capacitor
   - Mengoptimalkan pengalaman antar platform

## Aplikasi Hybrid vs Native vs Web App

| Fitur | Aplikasi Hybrid | Aplikasi Native | Web App |
|-------|----------------|----------------|---------|
| Akses ke hardware | Terbatas | Penuh | Sangat terbatas |
| Performa | Baik | Terbaik | Tergantung browser |
| Pengembangan | Cepat | Lambat | Sangat cepat |
| Ukuran aplikasi | Kecil-Sedang | Besar | Sangat kecil |
| Kompatibilitas | Tinggi | Terbatas per platform | Sangat tinggi |
| Instalasi | Opsional | Diperlukan | Tidak diperlukan |

## Pelajaran dari Proyek Ini

Mengembangkan BMI Calculator sebagai aplikasi hybrid menunjukkan bagaimana teknologi web modern dapat digunakan untuk membuat aplikasi yang fungsional dan menarik bahkan di perangkat mobile. Meskipun memiliki beberapa batasan dibandingkan dengan aplikasi native, pendekatan hybrid menawarkan keseimbangan yang baik antara kemudahan pengembangan dan fungsionalitas.

Proyek ini juga mendemonstrasikan bagaimana aplikasi sederhana dapat dikembangkan langsung di perangkat Android menggunakan Dcoder, menunjukkan potensi untuk pengembangan aplikasi mobile tanpa memerlukan komputer desktop.

## Lisensi

Proyek ini dilisensikan di bawah [MIT License](LICENSE).

## Kontak

Jika Anda memiliki pertanyaan atau saran, silakan hubungi:

- Email: nicholasrafa786@gmail.com
- GitHub: [Nicholas786](https://github.com/nicholas786)

---

*Proyek ini dibuat sebagai bagian dari tugas sekolah untuk mendemonstrasikan konsep aplikasi hybrid menggunakan Dcoder di Android.*
