# Tutorial Lengkap - Nota Dinas PUPR

## Deskripsi Aplikasi

**Nota Dinas** adalah aplikasi web modern untuk mengelola peminjaman barang dan kendaraan dinas di lingkungan **Kementerian Pekerjaan Umum dan Perumahan Rakyat (PUPR)**. Aplikasi ini memiliki sistem keamanan berbasis role dengan dua peran utama:

1. **Peminjam** - Dapat mengajukan permintaan peminjaman barang/kendaraan
2. **Approver** - Dapat meninjau dan menyetujui/menolak permintaan

### Fitur Utama yang Telah Diimplementasikan:
- ✅ **Sistem Login Aman** dengan username & password
- ✅ **Role-based Access Control** (Peminjam tidak bisa akses halaman Approver)
- ✅ **Logo Kementerian PUPR** terintegrasi di seluruh aplikasi
- ✅ **Tema Warna PUPR** (Biru dan Kuning) yang konsisten
- ✅ **Dashboard role-based** (Peminjam & Approver)
- ✅ **Form permintaan** dengan validasi lengkap
- ✅ **Sistem persetujuan** dengan status tracking
- ✅ **Berita Acara** untuk dokumentasi resmi
- ✅ **UI modern** dengan Tailwind CSS & ShadCN
- ✅ **Responsive design** untuk semua perangkat
- ✅ **Fungsi Logout** yang berfungsi dengan baik

---

## Cara Menjalankan Project di Lokal

### 1. Persyaratan Sistem
- **Node.js** versi 18 atau lebih baru
- **npm** atau **yarn** package manager
- **Git** (opsional, untuk clone repository)

### 2. Instalasi Dependencies

```bash
# Masuk ke direktori project
cd nota-dinas

# Install semua dependencies
npm install
```

### 3. Menjalankan Development Server

```bash
# Jalankan development server
npm run dev
```

Server akan berjalan di: **http://localhost:8000**

### 4. Build untuk Production

```bash
# Build aplikasi untuk production
npm run build

# Jalankan production server
npm start
```

---

## Akun Demo untuk Testing

Aplikasi dilengkapi dengan akun demo yang dapat digunakan untuk testing:

### Akun Peminjam:
- **Username:** `peminjam1` | **Password:** `peminjam123`
- **Username:** `peminjam2` | **Password:** `peminjam123`

### Akun Approver:
- **Username:** `approver1` | **Password:** `approver123`
- **Username:** `admin` | **Password:** `admin123`

---

## Panduan Penggunaan Aplikasi

### 1. Halaman Login
- Buka browser dan akses `http://localhost:8000`
- Masukkan username dan password sesuai role yang diinginkan
- Sistem akan otomatis mengarahkan ke dashboard yang sesuai
- **Keamanan:** Peminjam tidak bisa mengakses halaman Approver dan sebaliknya

### 2. Dashboard Peminjam (`/peminjam`)

#### Fitur:
- **Sambutan Personal** dengan nama lengkap user
- **Form Permintaan Peminjaman** dengan field:
  - Nama Lengkap (otomatis terisi dari data user)
  - Barang/Kendaraan (dropdown dengan pilihan)
  - Keperluan Dinas (textarea, minimal 10 karakter)
  - Tanggal Peminjaman (tidak boleh masa lalu)
- **Status Workflow** visual (Isi form → Menunggu → Disetujui)
- **Panduan Prosedur** dan ketentuan umum

#### Cara Menggunakan:
1. Login dengan akun peminjam
2. Isi semua field yang diperlukan (nama sudah otomatis terisi)
3. Pilih barang/kendaraan dari dropdown:
   - Mobil Dinas
   - Motor Dinas
   - Laptop
   - Proyektor
   - Kamera
   - Printer
   - Alat Tulis Kantor
   - Lainnya
4. Klik "Kirim Permintaan"
5. Sistem akan menampilkan pesan konfirmasi

### 3. Dashboard Approver (`/approver`)

#### Fitur:
- **Sambutan Personal** dengan nama lengkap approver
- **Statistik Dashboard** menampilkan:
  - Jumlah permintaan menunggu review
  - Jumlah permintaan disetujui
  - Jumlah permintaan ditolak
- **Filter Permintaan** berdasarkan status dengan tab berwarna
- **Aksi Persetujuan** untuk setiap permintaan
- **Panduan Approver** dengan kriteria dan tindakan yang diperlukan

#### Cara Menggunakan:
1. Login dengan akun approver
2. Lihat daftar permintaan yang masuk
3. Gunakan filter tab untuk menyaring berdasarkan status
4. Untuk setiap permintaan, klik:
   - **"Setujui"** untuk menyetujui permintaan
   - **"Tolak"** untuk menolak permintaan
5. Status akan otomatis terupdate

### 4. Berita Acara (`/berita-acara`)

#### Fitur:
- **Header Resmi** dengan logo Kementerian PUPR
- **Timestamp Otomatis** waktu pencetakan
- **Ringkasan Statistik** permintaan yang disetujui
- **Daftar Detail** semua permintaan yang disetujui
- **Fungsi Print/Download** untuk dokumentasi resmi
- **Format Profesional** siap untuk keperluan administrasi

#### Cara Menggunakan:
1. Akses halaman Berita Acara (tersedia untuk semua role)
2. Lihat ringkasan dan detail permintaan yang disetujui
3. Klik "Cetak / Download PDF" untuk mencetak dokumen
4. Dokumen siap untuk arsip atau keperluan administrasi

---

## Fitur Keamanan yang Diimplementasikan

### 1. Sistem Login:
- **Username & Password** untuk setiap user
- **Role-based Authentication** 
- **Session Management** dengan React Context
- **Auto-redirect** berdasarkan role user

### 2. Access Control:
- **Peminjam** hanya bisa akses `/peminjam` dan `/berita-acara`
- **Approver** hanya bisa akses `/approver` dan `/berita-acara`
- **Redirect otomatis** jika user mencoba akses halaman yang tidak diizinkan
- **Logout berfungsi** dengan baik dan menghapus session

### 3. Form Validation:
- **Nama**: Wajib diisi, minimal 2 karakter
- **Barang/Kendaraan**: Wajib dipilih dari dropdown
- **Keperluan**: Wajib diisi, minimal 10 karakter
- **Tanggal**: Wajib diisi, tidak boleh masa lalu

---

## Desain & Branding PUPR

### 1. Logo & Identitas:
- **Logo Kementerian PUPR** di navbar dan header
- **Nama lengkap kementerian** di semua halaman
- **Konsistensi branding** di seluruh aplikasi

### 2. Tema Warna:
- **Biru Primer**: `#1e40af` (Blue-700) untuk header dan tombol utama
- **Biru Sekunder**: `#3b82f6` (Blue-500) untuk aksen
- **Kuning Aksen**: `#eab308` (Yellow-500) untuk tombol logout dan highlight
- **Background**: Gradient biru ke kuning yang lembut
- **Kartu**: Background putih dengan border biru

### 3. Typography:
- **Font**: System fonts yang clean dan professional
- **Hierarchy**: Jelas dengan ukuran yang konsisten
- **Readability**: Kontras warna yang baik untuk aksesibilitas

---

## Struktur Project

```
nota-dinas/
├── src/
│   ├── app/                    # Next.js App Router
│   │   ├── layout.tsx         # Layout utama dengan AuthProvider
│   │   ├── page.tsx           # Halaman login
│   │   ├── peminjam/
│   │   │   └── page.tsx       # Dashboard Peminjam (Protected)
│   │   ├── approver/
│   │   │   └── page.tsx       # Dashboard Approver (Protected)
│   │   └── berita-acara/
│   │       └── page.tsx       # Halaman Berita Acara (Protected)
│   ├── components/            # Komponen React
│   │   ├── Navbar.tsx         # Navigation bar dengan logo PUPR
│   │   ├── LoginForm.tsx      # Form login dengan akun demo
│   │   ├── RequestForm.tsx    # Form permintaan dengan validasi
│   │   ├── RequestList.tsx    # Daftar permintaan dengan filter
│   │   └── RequestCard.tsx    # Card permintaan individual
│   ├── context/
│   │   └── AuthContext.tsx    # Authentication & role management
│   ├── lib/
│   │   └── api.ts            # Simulasi API functions
│   └── components/ui/         # ShadCN UI components
├── public/                    # Static assets
├── package.json              # Dependencies & scripts
├── next.config.ts           # Next.js configuration
└── TUTORIAL.md              # Tutorial lengkap ini
```

---

## Teknologi yang Digunakan

### Frontend Framework:
- **Next.js 15** - React framework dengan App Router
- **React 19** - Library UI
- **TypeScript** - Type safety

### Styling:
- **Tailwind CSS 4** - Utility-first CSS framework
- **ShadCN UI** - Pre-built component library
- **Custom PUPR Theme** - Warna biru dan kuning

### Authentication & State:
- **React Context** - Authentication & role management
- **React Hooks** - Local state management
- **Custom Login System** - Username/password based

### Form & Validation:
- **React Hook Form** - Form management
- **Zod** - Schema validation
- **@hookform/resolvers** - Form validation integration

---

## Testing & Quality Assurance

### Fitur yang Telah Ditest:
1. ✅ **Login System** - Semua akun demo berfungsi
2. ✅ **Role-based Access** - Peminjam tidak bisa akses halaman Approver
3. ✅ **Logout Function** - Berfungsi dengan baik
4. ✅ **Form Validation** - Semua validasi bekerja
5. ✅ **Responsive Design** - Tampil baik di berbagai ukuran layar
6. ✅ **Navigation** - Semua link dan redirect berfungsi
7. ✅ **Branding** - Logo dan tema warna konsisten

### Browser Compatibility:
- ✅ Chrome/Chromium
- ✅ Firefox
- ✅ Safari
- ✅ Edge

---

## Troubleshooting

### Port 8000 sudah digunakan:
```bash
# Matikan proses yang menggunakan port 8000
fuser -k 8000/tcp

# Atau gunakan port lain
PORT=3000 npm run dev
```

### Error saat npm install:
```bash
# Hapus node_modules dan package-lock.json
rm -rf node_modules package-lock.json

# Install ulang
npm install
```

### Build error:
```bash
# Clear Next.js cache
rm -rf .next

# Build ulang
npm run build
```

### Login tidak berfungsi:
- Pastikan menggunakan akun demo yang benar
- Cek console browser untuk error
- Pastikan JavaScript enabled

---

## Customization & Development

### Menambah User Baru:
Edit file `src/context/AuthContext.tsx`, bagian `users`:

```typescript
const users = [
  {
    username: "user_baru",
    password: "password123",
    role: "peminjam" as Role,
    name: "Nama Lengkap User"
  },
  // ... user lainnya
]
```

### Menambah Jenis Barang/Kendaraan:
Edit file `src/components/RequestForm.tsx`, bagian `itemOptions`:

```typescript
const itemOptions = [
  "Mobil Dinas",
  "Motor Dinas", 
  "Laptop",
  "Proyektor",
  // Tambahkan item baru di sini
  "Item Baru",
]
```

### Mengubah Tema Warna:
Edit file komponen untuk mengubah class Tailwind:
- `bg-blue-600` → `bg-green-600` (untuk mengubah warna primer)
- `text-blue-900` → `text-green-900` (untuk mengubah warna teks)

---

## Deployment

### Vercel (Recommended):
1. Push code ke GitHub
2. Connect repository di Vercel
3. Deploy otomatis
4. Set environment variables jika diperlukan

### Manual Deployment:
```bash
# Build aplikasi
npm run build

# Upload folder .next, public, dan package.json ke server
# Jalankan: npm start
```

---

## Roadmap & Future Enhancements

### Fitur yang Bisa Ditambahkan:
- 📧 **Email Notifications** untuk status permintaan
- 📱 **Mobile App** dengan React Native
- 🔐 **Advanced Authentication** dengan JWT
- 📊 **Dashboard Analytics** dengan charts
- 📄 **PDF Generation** untuk Berita Acara
- 🔍 **Search & Filter** yang lebih advanced
- 📅 **Calendar Integration** untuk jadwal peminjaman
- 💬 **Comment System** untuk komunikasi

---

## Support & Kontribusi

### Development:
- Fork repository
- Buat branch baru untuk fitur
- Submit pull request dengan deskripsi yang jelas

### Bug Report:
- Buat issue di GitHub
- Sertakan screenshot dan langkah reproduksi
- Cantumkan versi browser dan OS

### Contact:
- Email: admin@pupr.go.id
- Website: https://pu.go.id

---

## Lisensi

Project ini dibuat untuk **Kementerian Pekerjaan Umum dan Perumahan Rakyat** dan dapat digunakan untuk keperluan internal kementerian.

---

**🏛️ Nota Dinas - Kementerian PUPR**
**Membangun Indonesia yang Lebih Baik**

Untuk pertanyaan lebih lanjut, silakan hubungi tim IT Kementerian PUPR.
