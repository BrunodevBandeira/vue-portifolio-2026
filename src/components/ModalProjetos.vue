<template>
  <div>
    <h2 class="modal-title">Projetos</h2>

    <div v-for="section in sections" :key="section.id" class="projects-section">
      <h3>
        <i :class="section.icon" class="section-icon"></i>
        {{ section.label }}
      </h3>
      <div class="projects-grid">
        <a
          v-for="card in section.cards"
          :key="card.title"
          class="project-card"
          href="https://github.com/DevBrunoBandeira"
          target="_blank"
          rel="noopener noreferrer"
        >
          <div class="project-card-title">
            <i :class="card.icon"></i> {{ card.title }}
          </div>
          <div class="project-card-sub">{{ card.sub }}</div>
          <i class="fas fa-arrow-right project-card-arrow"></i>
        </a>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ModalProjetos',
  data() {
    return {
      sections: [
        {
          id: 'frontend',
          label: 'Frontend',
          icon: 'fas fa-palette',
          cards: [
            { title: 'Vue.js Projects',  icon: 'fab fa-vuejs',  sub: 'Interfaces modernas e responsivas' },
            { title: 'React Projects',   icon: 'fab fa-react',  sub: 'Componentes e SPAs com React' }
          ]
        },
        {
          id: 'backend',
          label: 'Backend',
          icon: 'fas fa-server',
          cards: [
            { title: 'Spring Boot APIs', icon: 'fab fa-java',      sub: 'REST APIs e microsserviços em Java' },
            { title: 'Banco de Dados',   icon: 'fas fa-database',  sub: 'PostgreSQL, Redis e MongoDB' }
          ]
        },
        {
          id: 'fullstack',
          label: 'Full Stack',
          icon: 'fas fa-layer-group',
          cards: [
            { title: 'Projetos Completos', icon: 'fas fa-rocket', sub: 'Do backend ao frontend integrado' },
            { title: 'RPA & Automação',    icon: 'fas fa-robot',  sub: 'Automação de processos e integrações' }
          ]
        }
      ]
    }
  }
}
</script>

<style scoped>
.modal-title {
  font-family: 'Cormorant Garamond', serif;
  font-size: 2rem;
  font-weight: 400;
  letter-spacing: 0.05em;
  margin-bottom: 28px;
  padding-bottom: 16px;
  border-bottom: 1px solid rgba(255, 255, 255, 0.1);
  color: #fff;
}

.projects-section h3 {
  font-family: 'Cormorant Garamond', serif;
  font-size: 1.1rem;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  color: rgba(255, 255, 255, 0.5);
  margin: 28px 0 16px;
  display: flex;
  align-items: center;
  gap: 8px;
}
.projects-section h3:first-of-type { margin-top: 0; }

.section-icon { color: #c9a96e; }

.projects-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 12px;
}

.project-card {
  display: block;
  text-decoration: none;
  color: inherit;
  border: 1px solid rgba(255, 255, 255, 0.1);
  border-radius: 8px;
  padding: 20px 24px;
  background: linear-gradient(135deg, rgba(255,255,255,0.04), rgba(255,255,255,0.01));
  transition: transform 0.3s ease, box-shadow 0.3s ease, border-color 0.3s ease;
  position: relative;
  overflow: hidden;
}

.project-card::before {
  content: '';
  position: absolute;
  inset: 0;
  background: linear-gradient(135deg, rgba(201, 169, 110, 0.08), transparent);
  opacity: 0;
  transition: opacity 0.3s;
}

.project-card:hover {
  transform: translateY(-4px);
  box-shadow: 0 20px 40px rgba(0,0,0,0.5), 0 0 0 1px rgba(201,169,110,0.3);
  border-color: rgba(201, 169, 110, 0.4);
}
.project-card:hover::before { opacity: 1; }

.project-card-title {
  font-size: 1rem;
  font-weight: 500;
  display: flex;
  align-items: center;
  gap: 10px;
  color: #fff;
}
.project-card-title i { color: #c9a96e; }

.project-card-sub {
  font-size: 0.82rem;
  color: rgba(255, 255, 255, 0.5);
  margin-top: 6px;
}

.project-card-arrow {
  position: absolute;
  right: 20px;
  top: 50%;
  transform: translateY(-50%);
  color: rgba(255, 255, 255, 0.3);
  transition: color 0.3s, transform 0.3s;
}
.project-card:hover .project-card-arrow {
  color: #c9a96e;
  transform: translateY(-50%) translateX(4px);
}

@media (max-width: 640px) {
  .projects-grid { grid-template-columns: 1fr; }
}
</style>
