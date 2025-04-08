# implementasi Desain Figma ke Website dengan React & Vite

## Teknologi dan Tools yang Digunakan
- **React**
adalah library JavaScript yang digunakan untuk membangun antarmuka pengguna berbasis komponen. React memudahkan pengembangan web karena:

- **Vite**
adalah build tool modern yang lebih cepat dibandingkan Create React App

- **React Router DOM**
Digunakan untuk menambahkan navigasi halaman di aplikasi React. Dengan ini, kita bisa membuka halaman seperti /home, /about, atau /contact tanpa reload.

- **CSS**
Proyek ini menggunakan file CSS terpisah untuk mengatur tampilan. Beberapa teknik styling yang digunakan:
    - Flexbox untuk menyusun layout.
    - Media query untuk responsivitas.
    - Transition & animation untuk efek visual (seperti floating CTA dan menu).

## Struktur Proyek

```
src/
│
├── assets/                # Gambar & aset lainnya
│   └── Profile.jpg
│
├── components/            # Komponen yang digunakan di banyak halaman
│   ├── CTA.jsx            # Tombol Call To Action (floating button)
│   ├── FloatingMenu.jsx   # Menu overlay fullscreen
│   └── Navbar.jsx         # Navigasi utama (Home, About, Contact)
│
├── pages/                 # Halaman utama
│   ├── About.jsx          # Halaman tentang (optional)
│   ├── Contact.jsx        # Halaman kontak
│   ├── Home.jsx           # Landing Page
│   └── LandingPage.jsx    # Komposisi halaman (gabungkan Home, Contact, dst)
│
├── styles/
│   └── index.css          # Styling global (warna, font, layout)
│
├── App.jsx                # Root komponen utama (memuat <LandingPage />)
└── main.jsx               # Entry point aplikasi, render App ke root DOM
```

## Penjelasan Kode/ Komponen
### Landing Page 
```jsx
function LandingPage() {
  const [isMenuOpen, setIsMenuOpen] = useState(false);

  const handleToggleMenu = () => {
    setIsMenuOpen(!isMenuOpen);
  };

  return (
    <div id="home">
      <Navbar />
      <Home />
      <About />
      <Contact />
      {!isMenuOpen && <CTA onClick={handleToggleMenu} />}
      <FloatingMenu isOpen={isMenuOpen} onClose={handleToggleMenu} />
    </div>
  );
}
```
- Menggunakan **React Hook** ``useState()`` untuk mengatur state ``isMenuOpen``, yang menentukan apakah ``FloatingMenu`` sedang ditampilkan atau tidak.
- Fungsi ``handleToggleMenu()`` digunakan untuk membuka atau menutup menu.
- Kondisi ``!isMenuOpen && <CTA />`` membuat tombol hanya muncul jika menu belum dibuka.
- Komponen ``FloatingMenu`` akan menerima props:
     - ``isOpen`` → status buka/tutup
    - ``onClose`` → fungsi untuk menutup menu saat tombol “X” diklik

### Home 
```jsx
function Home() {
  return (

     <div className="Home-wrapper">
    <section className="Home">
      <div className="Home-content">
        <h1>Flow Developer — <span className="highlight">UI/UX</span></h1>
      </div>
      <div className="Home-image">
      <img src={ProfileImg} alt="Profile" /> 
      </div>
    </section>
    </div>
  );
  ```

- ``<div className="Home-wrapper">`` dan ``<section className="Home"> ``digunakan untuk membungkus dan menata konten agar lebih terstruktur.
- ``<div className="Home-content">`` menampilkan teks judul.
- ``<div className="Home-image">`` menampilkan gambar profil.
- Class ``highlight`` digunakan untuk memberi warna khusus pada teks "UI/UX"

### About 
```jsx
function About() {
  return (
    <section id="about" className="about-section">
      <h2>About</h2>
      <p>
     Hi aku Andini.
     </p>
     <p>
    web ini diawali sebagai bagian dari tugas 
    web client Development dalam pengaplikasian react dan penggunaan vite.
    </p>
    <p>
    apakah hanya itu? tentu tidak 
    Sebagai creator aku akan terus berusaha mengembangkan web ini
      </p>
    </section>
  );
}
```
- ``<section>`` dengan ``id="about"`` membuat bagian ini bisa di-scroll langsung melalui anchor link di navbar ( ``#about``).
- Menggunakan class ``about-section`` untuk pengaturan layout dan styling seperti padding, warna, layout, dan responsivitas bagian ini.

### Contact 
Komponen ini dibagi menjadi dua bagian: kontak kiri (informasi kontak & sosial media) dan kontak kanan (formulir pesan).
```jsx
function Contact() {
  return (
    <section id="contact" className="contact-container">
      ...
    </section>
  );
}
```


**Bagian 1: contact-left (Kiri)**

Berisi informasi profil dan sosial media.
```jsx
<div className="contact-left">
  <img src={ProfileImg} alt="Profile" className="profile-img" />
  <div className="contact-info">
    <h3>Contact Details</h3>
    <p>Email dan Nomor HP</p>

    <h3>Social</h3>
    <ul>
      <li><a href="...">LinkedIn</a></li>
      <li><a href="...">Instagram</a></li>
      <li><a href="...">GitHub</a></li>
    </ul>
  </div>
</div>
```
**Fungsinya**
- Menampilkan foto profil pengguna (ProfileImg)
- Menyediakan informasi kontak (email, no HP)
- Menyediakan link ke sosial media (LinkedIn, Instagram, GitHub)



**Bagian 2: contact-right (Kanan)**

Berisi form input agar pengunjung bisa mengirim pesan
```jsx
<div className="contact-right">
  <h2>Let’s build something cool together</h2>
  <form className="contact-form">
    <label>Nama</label>
    <input type="text" placeholder="Nama Kamu" required />

    <label>Email</label>
    <input type="email" placeholder="emailkamu@gmai.com" required />

    <label>Subjek</label>
    <input type="text" placeholder="Contoh: Kerja sama proyek" />

    <label>Pesan</label>
    <textarea placeholder="Tulis pesan kamu di sini..." rows="5"></textarea>

    <button type="submit">Submit</button>
  </form>
</div>
```
**Fungsinya**
- Memberikan ajakan kolaborasi lewat teks
- Menyediakan form input yang terdiri dari: Nama, Email, Subjek dan Pesan
- Tombol Submit untuk mengirim pesan

## Kesimpulan
Proyek ini merupakan implementasi dari desain Figma ke dalam website nyata menggunakan React dan Vite sebagai tools utama. Dengan pendekatan komponen dan routing, website ini dibangun secara modular, efisien, dan mudah dikembangkan.

Selain itu, berbagai fitur seperti navigasi responsif, CTA button interaktif, dan form kontak menjadikan website ini tidak hanya fungsional, tapi juga memberikan pengalaman pengguna yang baik.

Web ini juga menjadi bukti kemampuan dalam:

    - Menerapkan konsep UI/UX dari desain ke kode
    - Mengelola struktur proyek React secara bersih
    - Menggunakan tools modern (Vite, React Router, CSS responsive)

Ke depannya, proyek ini masih sangat terbuka untuk dikembangkan lebih jauh, baik dari segi fitur, styling, maupun integrasi backend untuk form kontak dan lainnya.