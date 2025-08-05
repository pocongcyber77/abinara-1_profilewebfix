# 🚀 WEB_Abinara-1 - Website Profil Tim Robotik ITS
# TURUUUUUUUUUUUUUUUUUUUUUUUU SAYA NAK TIDOOOOOOOOOOO

![Vue.js](https://img.shields.io/badge/Vue.js-3.5.13-4FC08D?style=for-the-badge&logo=vue.js&logoColor=white)
![Vite](https://img.shields.io/badge/Vite-6.0.11-646CFF?style=for-the-badge&logo=vite&logoColor=white)
![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-4.0.6-38B2AC?style=for-the-badge&logo=tailwind-css&logoColor=white)
![pnpm](https://img.shields.io/badge/pnpm-8.0.0-F69220?style=for-the-badge&logo=pnpm&logoColor=white)

## 📋 Tentang Proyek

**WEB_Abinara-1** adalah website profil resmi tim robotik Abinara-1 dari Institut Teknologi Sepuluh Nopember (ITS). Website ini menampilkan informasi lengkap tentang tim, prestasi, anggota, robot, dan fitur workshop registration yang interaktif.

### 🎯 Fitur Utama

- **🏠 Landing Page Interaktif** - Hero section dengan flip animation dari gambar ke video YouTube
- **👥 Profil Tim** - Informasi lengkap anggota tim Abinara-1
- **🤖 Robot Gallery** - Galeri robot dengan slider interaktif
- **🏆 Achievement** - Prestasi dan pencapaian tim
- **📸 Gallery** - Dokumentasi kegiatan tim
- **🎓 Workshop Registration** - Form pendaftaran workshop "Advance Abinara 1.0"
- **📱 Responsive Design** - Optimal di semua device (Desktop, Tablet, Mobile)

### 🛠️ Teknologi yang Digunakan

- **Frontend Framework**: Vue.js 3 (Composition API)
- **Build Tool**: Vite 6.0.11
- **CSS Framework**: Tailwind CSS 4.0.6
- **Package Manager**: pnpm
- **UI Components**: PrimeVue 4.3.1
- **Carousel/Slider**: Swiper 11.2.4
- **Animations**: Animate.css + AOS (Animate On Scroll)
- **Linting**: ESLint + Prettier
- **Router**: Vue Router 4.5.0

## 🚀 Cara Memulai

### 📋 Prerequisites

Sebelum menjalankan proyek ini, pastikan Anda telah menginstall:

- **Node.js** (versi 18 atau lebih baru)
- **pnpm** (package manager)

### 🔧 Instalasi

1. **Clone Repository**
   ```bash
   git clone https://github.com/bielnzar/PROG_Web-Tim.git
   cd PROG_Web-Tim
   ```

2. **Install Dependencies**
   ```bash
   pnpm install
   ```

3. **Jalankan Development Server**
   ```bash
   pnpm dev
   ```

4. **Buka Browser**
   - Website akan berjalan di: `http://localhost:5173` (atau port lain jika 5173 sudah terpakai)
   - Halaman workshop: `http://localhost:5173/advance`

## 📁 Struktur Proyek

```
PROG_Web-Tim/
├── public/                 # Static assets
│   ├── poster.png         # Poster workshop
│   └── ...
├── src/
│   ├── assets/            # Assets (images, CSS)
│   │   ├── images/        # Gambar-gambar
│   │   └── css/           # Stylesheet
│   ├── components/        # Vue Components
│   │   ├── buttons/       # Komponen button
│   │   ├── profiles/      # Komponen profil
│   │   ├── page/          # Halaman-halaman
│   │   │   ├── home/      # Komponen homepage
│   │   │   └── ...        # Halaman lainnya
│   │   ├── FlipCard.vue   # Komponen flip animation
│   │   ├── WorkshopPopup.vue # Popup workshop
│   │   └── ...
│   ├── router/            # Vue Router configuration
│   ├── App.vue            # Root component
│   └── main.js            # Entry point
├── package.json           # Dependencies & scripts
├── vite.config.js         # Vite configuration
├── tailwind.config.js     # Tailwind CSS configuration
└── README.md              # Dokumentasi ini
```

## 🎮 Scripts yang Tersedia

```bash
# Development
pnpm dev          # Jalankan development server dengan hot-reload

# Build
pnpm build        # Build untuk production
pnpm preview      # Preview hasil build

# Code Quality
pnpm lint         # Lint dengan ESLint
pnpm format       # Format code dengan Prettier
```

## 🎨 Fitur Khusus

### 🎭 Flip Animation Hero Section
- **Auto-flip**: Gambar akan flip ke video YouTube setelah 2 detik
- **Hover-trigger**: Flip langsung saat mouse hover
- **Responsive**: Menyesuaikan ukuran di mobile dan desktop
- **Video**: Embed YouTube video `https://youtu.be/mr9PO-w45q0`

### 🎓 Workshop Registration System
- **Form Lengkap**: Nama, NRP, Email, Telepon, Fakultas, Departemen, Materi, Paket
- **Validasi**: Form validation dengan required fields
- **UI Elegan**: Design modern dengan gradient dan shadow
- **Responsive**: Optimal di semua device

### 🎪 Popup Workshop
- **Poster Display**: Menampilkan poster workshop dari `public/poster.png`
- **Card Design**: Frame card yang elegan
- **Navigation**: Link ke halaman registration form

## 📱 Responsive Design

Website ini dioptimalkan untuk berbagai ukuran layar:

- **Desktop** (≥1024px): Layout penuh dengan semua fitur
- **Tablet** (768px - 1023px): Layout menyesuaikan dengan touch interface
- **Mobile** (<768px): Layout mobile-first dengan navigasi yang mudah

## 🔧 Konfigurasi

### Environment Variables
Buat file `.env` di root directory untuk konfigurasi:

```env
VITE_APP_TITLE=WEB_Abinara-1
VITE_APP_DESCRIPTION=Website Profil Tim Robotik Abinara-1 ITS
```

### Tailwind CSS Configuration
File `tailwind.config.js` berisi konfigurasi custom untuk:
- Custom colors (Abinara red theme)
- Custom fonts
- Responsive breakpoints
- Animation utilities

## 🐛 Troubleshooting

### Masalah Umum

1. **Port 5173 sudah terpakai**
   ```bash
   # Vite akan otomatis mencari port lain
   # Atau gunakan port spesifik
   pnpm dev --port 3000
   ```

2. **Dependencies tidak terinstall**
   ```bash
   # Hapus node_modules dan reinstall
   rm -rf node_modules pnpm-lock.yaml
   pnpm install
   ```

3. **ESLint errors**
   ```bash
   # Auto-fix linting errors
   pnpm lint --fix
   ```

### Performance Tips

- Gunakan `pnpm` untuk install dependencies (lebih cepat dari npm)
- Aktifkan Vite's HMR (Hot Module Replacement) untuk development
- Optimize images sebelum upload ke `public/` folder

## 🤝 Kontribusi

Kami menyambut kontribusi dari siapa saja! Berikut cara berkontribusi:

1. **Fork** repository ini
2. **Create** branch baru (`git checkout -b feature/AmazingFeature`)
3. **Commit** perubahan (`git commit -m 'Add some AmazingFeature'`)
4. **Push** ke branch (`git push origin feature/AmazingFeature`)
5. **Open** Pull Request

### Guidelines untuk Kontribusi

- Ikuti coding style yang sudah ada
- Tambahkan komentar untuk kode yang kompleks
- Test fitur baru di berbagai browser
- Update dokumentasi jika diperlukan

## 📄 Lisensi

Proyek ini dilisensikan di bawah **MIT License** - lihat file [LICENSE](LICENSE) untuk detail.

## 👥 Tim Pengembang

**Abinara-1 Team** - Institut Teknologi Sepuluh Nopember (ITS)

- **Lead Developer**: [Nama Lead Developer]
- **Frontend Developer**: [Nama Frontend Developer]
- **UI/UX Designer**: [Nama Designer]
- **Content Writer**: [Nama Content Writer]

## 📞 Kontak

- **Website**: [abinara-beta.vercel.app](https://abinara-beta.vercel.app)
- **Email**: [email@abinara.its.ac.id]
- **Instagram**: [@abinara_its](https://instagram.com/abinara_its)
- **GitHub**: [bielnzar/PROG_Web-Tim](https://github.com/bielnzar/PROG_Web-Tim)

## 🙏 Ucapan Terima Kasih

Terima kasih kepada:
- **ITS** - Institut Teknologi Sepuluh Nopember
- **Vue.js Team** - Framework yang luar biasa
- **Tailwind CSS** - Utility-first CSS framework
- **Vite** - Build tool yang cepat
- **Semua kontributor** yang telah membantu pengembangan website ini

---

⭐ **Jika website ini membantu, jangan lupa berikan star di repository ini!** ⭐
