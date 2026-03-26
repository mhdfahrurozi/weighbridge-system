<script setup>
import { ref } from 'vue'

const appName = "Weighbridge Sawit Pro"
const version = "v1.2.0"
const downloadLink = "#" // Ganti dengan link file .exe kamu nanti

const features = [
  { title: 'Akurasi Tinggi', desc: 'Sistem kalkulasi otomatis Bruto, Tara, dan Netto tanpa celah error.' },
  { title: 'Penyimpanan Lokal', desc: 'Data tersimpan aman di perangkat meskipun tanpa koneksi internet.' },
  { title: 'Siap Cetak', desc: 'Format slip timbangan standar industri PKS (Pabrik Kelapa Sawit).' }
]
</script>

<template>
  <div class="landing-container">
    <nav class="navbar">
      <div class="logo font-black">WEIGHBRIDGE <span class="text-emerald">PRO</span></div>
      <div class="version-badge">{{ version }}</div>
    </nav>

    <header class="hero">
      <div class="hero-content">
        <h1 class="title">Kelola Timbangan Sawit <br> <span class="text-gradient">Lebih Cepat & Akurat</span></h1>
        <p class="subtitle">
          Solusi digital timbangan PKS modern. Pantau muatan, hitung potongan refraksi, 
          dan cetak slip otomatis dalam satu aplikasi desktop yang ringan.
        </p>

        <div class="cta-group">
          <a :href="downloadLink" class="btn-download">
            <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v4"/><polyline points="7 10 12 15 17 10"/><line x1="12" y1="15" x2="12" y2="3"/></svg>
            Download Installer (.exe)
          </a>
          <p class="os-info">Khusus Windows 10/11 • 64-bit</p>
        </div>
      </div>
    </header>

    <section class="features">
      <div v-for="(feat, index) in features" :key="index" class="feat-card">
        <h3>{{ feat.title }}</h3>
        <p>{{ feat.desc }}</p>
      </div>
    </section>

    <section class="security-note">
      <div class="note-box">
        <div class="icon">⚠️</div>
        <div>
          <h4>Catatan Instalasi</h4>
          <p>Jika muncul peringatan <i>"Windows Protected Your PC"</i>, klik <b>More Info</b> lalu <b>Run Anyway</b>. Ini terjadi karena aplikasi dalam tahap pengembangan (unverified publisher).</p>
        </div>
      </div>
    </section>

    <footer class="footer">
      <p>&copy; 2026 {{ appName }}. Built for PKS Indonesia.</p>
    </footer>
  </div>
</template>

<style scoped>
/* Reset & Base */
.landing-container {
  font-family: 'Inter', sans-serif;
  background-color: #0f172a;
  color: #f1f5f9;
  min-height: 100vh;
  padding: 0 2rem;
}

.text-emerald { color: #10b981; }
.font-black { font-weight: 900; }

/* Navbar */
.navbar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 2rem 0;
  max-width: 1000px;
  margin: 0 auto;
}

.version-badge {
  background: rgba(16, 185, 129, 0.1);
  color: #10b981;
  padding: 4px 12px;
  border-radius: 99px;
  font-size: 12px;
  font-weight: bold;
  border: 1px solid rgba(16, 185, 129, 0.3);
}

/* Hero */
.hero {
  text-align: center;
  padding: 6rem 0;
  max-width: 800px;
  margin: 0 auto;
}

.title {
  font-size: 3.5rem;
  font-weight: 900;
  line-height: 1.1;
  margin-bottom: 1.5rem;
}

.text-gradient {
  background: linear-gradient(to right, #10b981, #3b82f6);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}

.subtitle {
  font-size: 1.2rem;
  color: #94a3b8;
  margin-bottom: 3rem;
  line-height: 1.6;
}

/* CTA Button */
.btn-download {
  display: inline-flex;
  align-items: center;
  gap: 12px;
  background-color: #10b981;
  color: white;
  padding: 1.2rem 2.5rem;
  border-radius: 1rem;
  font-weight: 800;
  text-decoration: none;
  font-size: 1.1rem;
  transition: all 0.3s ease;
  box-shadow: 0 10px 25px -5px rgba(16, 185, 129, 0.4);
}

.btn-download:hover {
  transform: translateY(-3px);
  box-shadow: 0 20px 30px -10px rgba(16, 185, 129, 0.5);
  background-color: #059669;
}

.os-info {
  margin-top: 12px;
  font-size: 12px;
  color: #475569;
}

/* Features */
.features {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 2rem;
  max-width: 1000px;
  margin: 4rem auto;
}

.feat-card {
  background: rgba(30, 41, 59, 0.5);
  padding: 2rem;
  border-radius: 1.5rem;
  border: 1px solid #1e293b;
}

.feat-card h3 {
  color: #fff;
  margin-bottom: 10px;
}

.feat-card p {
  color: #94a3b8;
  font-size: 14px;
}

/* Security Note */
.security-note {
  max-width: 1000px;
  margin: 0 auto 4rem;
}

.note-box {
  display: flex;
  gap: 1.5rem;
  background: rgba(245, 158, 11, 0.05);
  border: 1px solid rgba(245, 158, 11, 0.2);
  padding: 1.5rem;
  border-radius: 1rem;
  align-items: center;
}

.note-box h4 { color: #f59e0b; margin-bottom: 5px; }
.note-box p { font-size: 13px; color: #94a3b8; }
.note-box .icon { font-size: 2rem; }

.footer {
  text-align: center;
  padding: 4rem 0;
  color: #475569;
  font-size: 13px;
  border-top: 1px solid #1e293b;
}
</style>