<script setup>
import { ref } from 'vue'

const appName = "Weighbridge Sawit System"
const version = "v1.0.1"
const downloadLink = "/WeighBridge-Sawit.exe" 

const features = [
  { icon: '🌴', title: 'Akurasi Digital PKS', desc: 'Kalkulasi otomatis Bruto, Tara, Netto, dan Potongan Refraksi standar pabrik.' },
  { icon: '💾', title: 'Mode Offline Handal', desc: 'Data tersimpan aman di database lokal perangkat tanpa butuh koneksi internet.' },
  { icon: '🖨️', title: 'Cetak Slip Standar', desc: 'Format struk timbangan profesional, siap cetak untuk supir dan arsip.' }
]

const installationSteps = [
  {
    title: "1. Unduh & Jalankan Installer",
    desc: "Klik tombol download di atas untuk mendapatkan file .exe. Setelah selesai, buka file tersebut untuk memulai proses instalasi simulasi.",
    img: "step1.png", 
    isLeft: true
  },
  {
    title: "2. Verifikasi SmartScreen",
    desc: "Jika muncul peringatan Windows, jangan khawatir. Klik 'More Info' lalu pilih 'Run Anyway' untuk melanjutkan ke dashboard simulasi timbangan.",
    img: "step2.png", 
    isLeft: false
  },
  {
    title: "3. Aplikasi Siap Digunakan",
    desc: "Setelah terbuka, Anda dapat langsung melakukan simulasi input data kendaraan, penimbangan bruto/tara, hingga mencetak slip bukti timbang.",
    img: "step3.png", 
    isLeft: true
  }
]
</script>

<template>
  <div class="sawit-landing-page">
    <div class="overlay"></div> 
    
    <div class="content-wrapper">
      <nav class="navbar">
        <div class="logo font-black">
          🌴 WEIGHBRIDGE <span class="text-emerald">SYSTEM</span>
        </div>
        <div class="flex items-center gap-4">
          <span class="version-tag">{{ version }}</span>
          <a :href="downloadLink" class="btn-nav-download">Download</a>
        </div>
      </nav>

      <header class="hero-section">
        <div class="hero-text">
          <h1 class="main-title">
            Simulasi Digital Timbangan Muatan Sawit <br>
            <span class="text-highlight">Cepat, Akurat, & Universal</span>
          </h1>
          <p class="main-subtitle">
            Aplikasi simulasi ini memfasilitasi integrasi data berat masuk dan keluar secara sistematis. Pelajari cara menghasilkan perhitungan netto yang presisi dan pencetakan struk bukti timbang instan secara offline.
          </p>

          <div class="cta-container">
            <a :href="downloadLink" download="Weighbridge-Sawit-Setup.exe" class="btn-main-download">
              <svg xmlns="http://www.w3.org/2000/svg" class="icon-dl" viewBox="0 0 20 20" fill="currentColor">
                <path fill-rule="evenodd" d="M3 17a1 1 0 011-1h12a1 1 0 110 2H4a1 1 0 01-1-1zm3.293-7.707a1 1 0 011.414 0L9 10.586V3a1 1 0 112 0v7.586l1.293-1.293a1 1 0 111.414 1.414l-3 3a1 1 0 01-1.414 0l-3-3a1 1 0 010-1.414z" clip-rule="evenodd" />
              </svg>
              Download Installer (.exe)
            </a>
            <p class="os-compatibility">Kompatibel dengan Windows 10 & 11 (64-bit)</p>
          </div>
        </div>
      </header>

      <section class="features-grid">
        <div v-for="(feat, index) in features" :key="index" class="feature-card">
          <div class="feat-icon">{{ feat.icon }}</div>
          <h3 class="feat-title">{{ feat.title }}</h3>
          <p class="feat-desc">{{ feat.desc }}</p>
        </div>
      </section>

      <section class="install-section">
        <h2 class="section-title">Tahapan Instalasi Aplikasi</h2>
        
        <div v-for="(step, index) in installationSteps" :key="index" 
             :class="['step-row', step.isLeft ? 'row-normal' : 'row-reverse']">
          
          <div class="step-text">
            <h3 class="text-emerald">{{ step.title }}</h3>
            <p>{{ step.desc }}</p>
          </div>

          <div class="step-image">
            <div class="img-frame">
              <img :src="step.img" :alt="step.title" @error="(e) => e.target.src = 'https://via.placeholder.com/600x350/1e293b/ffffff?text=Screenshot+Simulasi'">
            </div>
          </div>
        </div>
      </section>

      <section class="security-info">
        <div class="info-box">
          <span class="info-icon">💡</span>
          <p>
            <strong>Catatan Keamanan:</strong> Jika Windows menampilkan peringatan <em>"Unknown Publisher"</em> saat instalasi, 
            silahkan klik <strong>"More Info"</strong> lalu <strong>"Run Anyway"</strong>. Aplikasi ini aman dan sedang dalam tahap pengembangan aktif.
          </p>
        </div>
      </section>

      <footer class="main-footer">
        <p>&copy; 2026 Weighbridge Sawit - BDI Medan. Optimal untuk Pelatihan simulasi Industri Kelapa Sawit Indonesia.</p>
      </footer>
    </div>
  </div>
</template>

<style scoped>
/* FIX: Reset Global Body untuk memastikan background Full Screen */
:global(body) {
  margin: 0 !important;
  padding: 0 !important;
  overflow-x: hidden;
  width: 100%;
}

/* FIX: Menghapus pembatasan lebar dari bawaan Vue/Vite */
:global(#app) {
  max-width: 100% !important;
  margin: 0 !important;
  padding: 0 !important;
  text-align: left;
}

.sawit-landing-page {
  font-family: 'Inter', sans-serif;
  position: relative;
  min-height: 100vh;
  width: 100vw;
  background-image: url('https://images.unsplash.com/photo-1596716766488-8869c94025a1?q=80&w=2000&auto=format&fit=crop'); 
  background-size: cover;
  background-position: center;
  background-attachment: fixed;
  color: #fff;
  overflow-x: hidden;
}

.overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(15, 23, 42, 0.85); /* Sedikit lebih gelap agar teks lebih kontras */
  z-index: 1;
}

.content-wrapper {
  position: relative;
  z-index: 2;
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 2rem;
  display: flex;
  flex-direction: column;
}

/* UTILITY */
.text-emerald { color: #10b981; }
.text-center { text-align: center; }
.font-black { font-weight: 900; }
.flex { display: flex; }
.items-center { align-items: center; }
.gap-4 { gap: 1rem; }

/* NAVBAR */
.navbar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 1.5rem 0;
  border-bottom: 1px solid rgba(255, 255, 255, 0.1);
}

.logo {
  font-size: 1.25rem;
  letter-spacing: -1px;
}

.version-tag {
  font-size: 0.75rem;
  font-family: monospace;
  color: rgba(255, 255, 255, 0.5);
  background: rgba(255, 255, 255, 0.05);
  padding: 3px 8px;
  border-radius: 4px;
}

.btn-nav-download {
  text-decoration: none;
  color: #fff;
  font-size: 0.875rem;
  font-weight: 600;
  background: #10b981;
  padding: 8px 16px;
  border-radius: 8px;
  transition: all 0.2s;
}
.btn-nav-download:hover { background: #059669; }

/* HERO */
.hero-section {
  padding: 8rem 0 6rem;
  text-align: center;
}

.main-title {
  font-size: 3.5rem;
  font-weight: 900;
  line-height: 1.1;
  letter-spacing: -2px;
  margin-bottom: 1.5rem;
}

.text-highlight { color: #34d399; }

.main-subtitle {
  font-size: 1.125rem;
  color: rgba(255, 255, 255, 0.7);
  max-width: 800px;
  margin: 0 auto 3rem;
  line-height: 1.6;
}

/* BUTTON DOWNLOAD */
.cta-container {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.btn-main-download {
  display: inline-flex;
  align-items: center;
  gap: 12px;
  text-decoration: none;
  color: #fff;
  font-size: 1.125rem;
  font-weight: 800;
  background: #10b981;
  padding: 1.25rem 2.5rem;
  border-radius: 1rem;
  box-shadow: 0 10px 30px rgba(16, 185, 129, 0.4);
  transition: all 0.3s ease;
}

.btn-main-download:hover {
  transform: translateY(-4px);
  background: #059669;
  box-shadow: 0 20px 40px rgba(16, 185, 129, 0.5);
}

.icon-dl { width: 24px; height: 24px; }
.os-compatibility { margin-top: 12px; font-size: 0.75rem; color: rgba(255, 255, 255, 0.4); }

/* FEATURES */
.features-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 1.5rem;
  margin-bottom: 6rem;
}

.feature-card {
  background: rgba(255, 255, 255, 0.03);
  border: 1px solid rgba(255, 255, 255, 0.08);
  padding: 2.5rem;
  border-radius: 1.5rem;
  backdrop-filter: blur(10px);
}

.feat-icon { font-size: 2.5rem; margin-bottom: 1.5rem; }
.feat-title { font-size: 1.25rem; font-weight: 700; margin-bottom: 0.75rem; }
.feat-desc { font-size: 0.95rem; color: rgba(255, 255, 255, 0.6); line-height: 1.6; }

/* INSTALLATION STEPS */
.install-section { padding: 4rem 0 8rem; }
.section-title { font-size: 2.5rem; font-weight: 900; margin-bottom: 5rem; text-align: center; }

.step-row {
  display: flex;
  align-items: center;
  gap: 5rem;
  margin-bottom: 8rem;
}

.row-normal { flex-direction: row; }
.row-reverse { flex-direction: row-reverse; }

.step-text { flex: 1; }
.step-text h3 { font-size: 2rem; font-weight: 800; margin-bottom: 1.5rem; }
.step-text p { font-size: 1.15rem; line-height: 1.8; color: rgba(255, 255, 255, 0.7); }

.step-image { flex: 1.2; }
.img-frame {
  background: rgba(255, 255, 255, 0.05);
  padding: 12px;
  border-radius: 2rem;
  border: 1px solid rgba(255, 255, 255, 0.1);
  box-shadow: 0 40px 80px -20px rgba(0, 0, 0, 0.6);
}
.img-frame img { width: 100%; height: auto; border-radius: 1.2rem; display: block; }

/* SECURITY INFO */
.security-info { margin-bottom: 6rem; }
.info-box {
  display: flex;
  gap: 1.5rem;
  align-items: center;
  background: rgba(52, 211, 153, 0.05);
  border: 1px solid rgba(52, 211, 153, 0.2);
  padding: 1.5rem 2rem;
  border-radius: 1.2rem;
}
.info-icon { font-size: 1.5rem; }
.info-box p { font-size: 0.9rem; color: rgba(255, 255, 255, 0.7); margin: 0; line-height: 1.6; }

/* FOOTER */
.main-footer {
  text-align: center;
  padding: 3rem 0;
  border-top: 1px solid rgba(255, 255, 255, 0.05);
  font-size: 0.85rem;
  color: rgba(255, 255, 255, 0.4);
}

/* RESPONSIVE */
@media (max-width: 992px) {
  .main-title { font-size: 2.5rem; }
  .step-row { flex-direction: column !important; text-align: center; gap: 3rem; }
  .hero-section { padding: 5rem 0; }
}
</style>