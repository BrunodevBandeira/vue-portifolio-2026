<template>
  <section class="hero">
    <div class="hero-bg"></div>

    <div class="hero-content">
      <span class="line-top"></span>
      <div class="title-block">
        <h1>Bruno Bandeira</h1>
        <h2>Desenvolvedor Full Stack</h2>
      </div>
      <span class="line-bottom"></span>
    </div>

    <nav class="nav-tabs">
      <button
        v-for="tab in tabs"
        :key="tab.id"
        class="nav-tab"
        :class="{ active: activeTab === tab.id }"
        @click="$emit('open-tab', tab.id)"
      >
        {{ tab.label }}
      </button>
    </nav>

    <a
      class="cv-download"
      href="/BRUNO BANDEIRA - FULL STACK.pdf"
      download="BRUNO BANDEIRA - FULL STACK.pdf"
    >
      <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"/><polyline points="7 10 12 15 17 10"/><line x1="12" y1="15" x2="12" y2="3"/></svg>
      Baixar CV
    </a>
  </section>
</template>

<script>
export default {
  name: 'HeroSection',
  emits: ['open-tab'],
  props: {
    activeTab: {
      type: String,
      default: null
    }
  },
  data() {
    return {
      tabs: [
        { id: 'sobre',       label: 'Sobre' },
        { id: 'contato',     label: 'Contato' },
        { id: 'projetos',    label: 'Projetos' },
        { id: 'experiencia', label: 'Experiência' }
      ]
    }
  }
}
</script>

<style scoped>
.hero {
  position: relative;
  width: 100vw;
  height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  overflow: hidden;
}

.hero-bg {
  position: absolute;
  inset: 0;
  background: url('https://images.unsplash.com/photo-1537819191377-d3305ffddce4?q=80&w=1121&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D') center/cover no-repeat;
  filter: brightness(0.55);
  transform: scale(1.08);
  animation: zoomOut 20s ease-out forwards;
}

@keyframes zoomOut {
  from { transform: scale(1.08); }
  to   { transform: scale(1.00); }
}

.hero-content {
  position: relative;
  z-index: 2;
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 520px;
}

/* ── LINHAS ANIMADAS ── */
.line-top,
.line-bottom {
  display: block;
  width: 100%;
  height: 1px;
  background: rgba(255, 255, 255, 0.7);
  opacity: 0;
  animation: lineRevealTop 1.4s cubic-bezier(0.4, 0, 0.2, 1) 0.3s forwards;
}

.line-bottom {
  animation-name: lineRevealBottom;
  animation-delay: 0.3s;
}

@keyframes lineRevealTop {
  from { opacity: 0; transform: translateY(18px); }
  to   { opacity: 1; transform: translateY(0);    }
}

@keyframes lineRevealBottom {
  from { opacity: 0; transform: translateY(-18px); }
  to   { opacity: 1; transform: translateY(0);     }
}

.title-block {
  padding: 22px 0;
  text-align: center;
  opacity: 0;
  animation: fadeUp 1s ease 0.7s forwards;
}

@keyframes fadeUp {
  from { opacity: 0; transform: translateY(12px); }
  to   { opacity: 1; transform: translateY(0);    }
}

.title-block h1 {
  font-family: 'Cormorant Garamond', serif;
  font-size: clamp(2rem, 4vw, 3.2rem);
  font-weight: 300;
  letter-spacing: 0.06em;
  line-height: 1.2;
  color: #fff;
}

.title-block h2 {
  font-family: 'Cormorant Garamond', serif;
  font-size: clamp(1.4rem, 2.8vw, 2.2rem);
  font-weight: 300;
  letter-spacing: 0.1em;
  color: rgba(255, 255, 255, 0.85);
}

/* ── NAV TABS ── */
.nav-tabs {
  position: relative;
  z-index: 2;
  display: flex;
  margin-top: 44px;
  opacity: 0;
  animation: fadeUp 1s ease 1.1s forwards;
}

.nav-tab {
  padding: 12px 36px;
  border: 1px solid rgba(255, 255, 255, 0.5);
  background: rgba(0, 0, 0, 0.35);
  color: #fff;
  font-family: 'Outfit', sans-serif;
  font-size: 0.85rem;
  font-weight: 500;
  letter-spacing: 0.08em;
  cursor: pointer;
  transition: background 0.3s, border-color 0.3s;
  backdrop-filter: blur(8px);
}

.nav-tab:not(:last-child) { border-right: none; }
.nav-tab:first-child      { border-radius: 2px 0 0 2px; }
.nav-tab:last-child       { border-radius: 0 2px 2px 0; border-right: 1px solid rgba(255,255,255,0.5); }

.nav-tab:hover,
.nav-tab.active {
  background: rgba(255, 255, 255, 0.18);
  border-color: #fff;
}

.cv-download {
  position: relative;
  z-index: 2;
  display: inline-flex;
  align-items: center;
  gap: 8px;
  margin-top: 20px;
  padding: 10px 28px;
  border: 1px solid rgba(255, 255, 255, 0.4);
  border-radius: 2px;
  background: rgba(0, 0, 0, 0.3);
  color: rgba(255, 255, 255, 0.85);
  font-family: 'Outfit', sans-serif;
  font-size: 0.78rem;
  font-weight: 500;
  letter-spacing: 0.12em;
  text-decoration: none;
  text-transform: uppercase;
  cursor: pointer;
  backdrop-filter: blur(8px);
  transition: background 0.3s, border-color 0.3s, color 0.3s;
  opacity: 0;
  animation: fadeUp 1s ease 1.3s forwards;
}

.cv-download svg {
  width: 14px;
  height: 14px;
}

.cv-download:hover {
  background: rgba(255, 255, 255, 0.18);
  border-color: #fff;
  color: #fff;
}

@media (max-width: 640px) {
  .hero-content { width: 90vw; }
  .nav-tab { padding: 10px 18px; font-size: 0.78rem; }
  .cv-download { padding: 9px 20px; font-size: 0.72rem; }
}
</style>
