<template>
  <div>
    <div class="modal-header">
      <h2 class="modal-title">{{ view === 'grid' ? 'Projetos' : categoriaAtual.label }}</h2>
      <button v-if="view === 'detail'" class="btn-voltar" @click="view = 'grid'">
        <i class="fas fa-arrow-left"></i> Voltar
      </button>
    </div>

    <!-- ── GRID DE CARDS ── -->
    <template v-if="view === 'grid'">
      <div v-for="section in sections" :key="section.id" class="projects-section">
        <h3>
          <i :class="section.icon" class="section-icon"></i>
          {{ section.label }}
        </h3>
        <div class="projects-grid">
          <button
            v-for="card in section.cards"
            :key="card.id"
            class="project-card"
            @click="abrirCategoria(card.id)"
          >
            <div class="project-card-title">
              <i :class="card.icon"></i> {{ card.title }}
            </div>
            <div class="project-card-sub">{{ card.sub }}</div>
            <i class="fas fa-arrow-right project-card-arrow"></i>
          </button>
        </div>
      </div>
    </template>

    <!-- ── LISTA DE PROJETOS DA CATEGORIA ── -->
    <template v-else>
      <!-- Sem projetos -->
      <div v-if="categoriaAtual.projetos.length === 0" class="empty-state">
        <i class="fas fa-folder-open empty-icon"></i>
        <p>Nenhum projeto disponível nesta categoria ainda.</p>
        <span>Em breve...</span>
      </div>

      <!-- Com projetos -->
      <div v-else class="proj-list">
        <a
          v-for="(proj, index) in categoriaAtual.projetos"
          :key="proj.nome"
          class="proj-item"
          :class="{ 'last': index === categoriaAtual.projetos.length - 1 }"
          :href="proj.link"
          target="_blank"
          rel="noopener noreferrer"
        >
          <div class="proj-left">
            <span class="proj-nome">{{ proj.nome }}</span>
          </div>
          <div class="proj-right">
            <p class="proj-desc">{{ proj.descricao }}</p>
            <div class="tag-list">
              <span v-for="tag in proj.tags" :key="tag" class="tag">{{ tag }}</span>
            </div>
          </div>
          <i class="fas fa-arrow-right proj-arrow"></i>
        </a>
      </div>
    </template>
  </div>
</template>

<script>
export default {
  name: 'ModalProjetos',
  data() {
    return {
      view: 'grid',
      categoriaId: null,

      sections: [
        {
          id: 'frontend',
          label: 'Frontend',
          icon: 'fas fa-palette',
          cards: [
            { id: 'vuejs',  title: 'Vue.js Projects', icon: 'fab fa-vuejs',  sub: 'Interfaces modernas e responsivas' }
          ]
        },
        {
          id: 'backend',
          label: 'Backend',
          icon: 'fas fa-server',
          cards: [
            { id: 'springboot', title: 'Spring Boot APIs', icon: 'fab fa-java',     sub: 'REST APIs e microsserviços em Java' }
          ]
        },
        {
          id: 'fullstack',
          label: 'Full Stack',
          icon: 'fas fa-layer-group',
          cards: [
            { id: 'fullstack', title: 'FullStack',      icon: 'fas fa-rocket', sub: 'Do backend ao frontend integrado' },
            { id: 'rpa',       title: 'Microserviços', icon: 'fas fa-robot',  sub: 'Automação de processos e integrações' }
          ]
        }
      ],

      categorias: {
        vuejs: {
          label: 'Vue.js Projects',
          projetos: [
            {
              nome: 'Bike Shop',
              descricao: 'Landing page de loja de bicicletas com design moderno, apresentando produtos, serviços e seções de destaque com Vue.js.',
              tags: ['Vue.js', 'JavaScript', 'CSS', 'Vite'],
              link: 'https://github.com/BrunodevBandeira/bike-shop'
            },
            {
              nome: 'Café Projeto',
              descricao: 'Site institucional para cafeteria com páginas de cardápio, sobre e contato, desenvolvido com Vue Router e Bootstrap.',
              tags: ['Vue.js', 'Vue Router', 'Bootstrap', 'Vite'],
              link: 'https://github.com/BrunodevBandeira/cafe-projeto'
            },
            {
              nome: 'Cafeteria App',
              descricao: 'Aplicação completa de cafeteria com catálogo de produtos e interface responsiva construída com Vue.js.',
              tags: ['Vue.js', 'JavaScript', 'CSS', 'Vite'],
              link: 'https://github.com/BrunodevBandeira/cafeteria-app'
            }
          ]
        },
        springboot: {
          label: 'Spring Boot APIs',
          projetos: [
            {
              nome: 'Desafio Senha Segura',
              descricao: 'API REST para validação e gerenciamento de senhas seguras, aplicando boas práticas de segurança e design de software.',
              tags: ['Java', 'Spring Boot', 'REST API', 'Segurança'],
              link: 'https://github.com/BrunodevBandeira/Desafio-senhasegura'
            },
            {
              nome: 'Desafio Criptografia',
              descricao: 'Backend focado em criptografia de dados sensíveis, implementando algoritmos de encriptação para proteção de informações em banco de dados.',
              tags: ['Java', 'Spring Boot', 'Criptografia', 'JPA'],
              link: 'https://github.com/BrunodevBandeira/desafio-criptografia'
            },
            {
              nome: 'Desafio Empréstimo',
              descricao: 'API de simulação e controle de empréstimos com regras de negócio para cálculo de parcelas, taxas e elegibilidade.',
              tags: ['Java', 'Spring Boot', 'REST API', 'Regras de Negócio'],
              link: 'https://github.com/BrunodevBandeira/Desafio-emprestimo'
            }
          ]
        },
        fullstack: {
          label: 'FullStack',
          projetos: [
            {
              nome: 'Projeto Cadastro',
              descricao: 'Aplicação completa de cadastro de pessoas com Spring Boot no backend, Vue.js no frontend, MySQL como banco de dados e infraestrutura containerizada com Docker.',
              tags: ['Spring Boot', 'Vue.js', 'MySQL', 'Docker', 'REST API'],
              link: 'https://github.com/BrunodevBandeira/projeto-cadastro'
            }
          ]
        },
        rpa: {
          label: 'Microserviços',
          projetos: []
        }
      }
    }
  },

  computed: {
    categoriaAtual() {
      return this.categorias[this.categoriaId] || { label: '', projetos: [] }
    }
  },

  methods: {
    abrirCategoria(id) {
      this.categoriaId = id
      this.view = 'detail'
    }
  }
}
</script>

<style scoped>
.modal-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 28px;
  padding-bottom: 16px;
  border-bottom: 1px solid rgba(255, 255, 255, 0.1);
}

.modal-title {
  font-family: 'Cormorant Garamond', serif;
  font-size: 2rem;
  font-weight: 400;
  letter-spacing: 0.05em;
  color: #fff;
  margin: 0;
}

.btn-voltar {
  display: flex;
  align-items: center;
  gap: 8px;
  background: none;
  border: 1px solid rgba(255, 255, 255, 0.15);
  border-radius: 6px;
  color: rgba(255, 255, 255, 0.6);
  font-size: 0.8rem;
  padding: 6px 14px;
  cursor: pointer;
  transition: border-color 0.2s, color 0.2s;
  white-space: nowrap;
}
.btn-voltar:hover {
  border-color: #c9a96e;
  color: #c9a96e;
}

/* ── GRID DE CARDS ── */
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
  width: 100%;
  text-align: left;
  background: linear-gradient(135deg, rgba(255,255,255,0.04), rgba(255,255,255,0.01));
  border: 1px solid rgba(255, 255, 255, 0.1);
  border-radius: 8px;
  padding: 20px 24px;
  color: inherit;
  cursor: pointer;
  transition: transform 0.3s ease, box-shadow 0.3s ease, border-color 0.3s ease;
  position: relative;
  overflow: hidden;
}
.project-card::before {
  content: '';
  position: absolute;
  inset: 0;
  background: linear-gradient(135deg, rgba(201,169,110,0.08), transparent);
  opacity: 0;
  transition: opacity 0.3s;
}
.project-card:hover {
  transform: translateY(-4px);
  box-shadow: 0 20px 40px rgba(0,0,0,0.5), 0 0 0 1px rgba(201,169,110,0.3);
  border-color: rgba(201,169,110,0.4);
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
  color: rgba(255,255,255,0.5);
  margin-top: 6px;
}

.project-card-arrow {
  position: absolute;
  right: 20px;
  top: 50%;
  transform: translateY(-50%);
  color: rgba(255,255,255,0.3);
  transition: color 0.3s, transform 0.3s;
}
.project-card:hover .project-card-arrow {
  color: #c9a96e;
  transform: translateY(-50%) translateX(4px);
}

/* ── LISTA DE PROJETOS ── */
.proj-list {
  display: flex;
  flex-direction: column;
}

.proj-item {
  display: grid;
  grid-template-columns: 180px 1fr 24px;
  gap: 24px;
  padding: 24px 0;
  border-bottom: 1px solid rgba(255,255,255,0.07);
  text-decoration: none;
  color: inherit;
  position: relative;
  border-radius: 4px;
  transition: opacity 0.2s;
}
.proj-item::before {
  content: '';
  position: absolute;
  left: 170px;
  top: 0;
  bottom: 0;
  width: 1px;
  background: rgba(255,255,255,0.07);
}
.proj-item.last { border-bottom: none; }
.proj-item:hover .proj-nome { color: #e8c98e; }
.proj-item:hover .proj-arrow { color: #c9a96e; transform: translateX(4px); }

.proj-left {
  display: flex;
  flex-direction: column;
  justify-content: center;
  padding-right: 16px;
}

.proj-nome {
  font-family: 'Cormorant Garamond', serif;
  font-size: 1.05rem;
  font-weight: 600;
  color: #c9a96e;
  letter-spacing: 0.04em;
  transition: color 0.2s;
}

.proj-desc {
  font-size: 0.9rem;
  line-height: 1.75;
  color: rgba(255,255,255,0.75);
  font-weight: 300;
  margin: 0;
}

.tag-list {
  display: flex;
  flex-wrap: wrap;
  gap: 6px;
  margin-top: 10px;
}

.tag {
  font-size: 0.72rem;
  padding: 3px 10px;
  border: 1px solid rgba(255,255,255,0.15);
  border-radius: 20px;
  color: rgba(255,255,255,0.55);
  letter-spacing: 0.05em;
}

.proj-arrow {
  align-self: center;
  color: rgba(255,255,255,0.2);
  font-size: 0.85rem;
  transition: color 0.2s, transform 0.2s;
}

/* ── EMPTY STATE ── */
.empty-state {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding: 60px 20px;
  gap: 12px;
  text-align: center;
}
.empty-icon {
  font-size: 2.5rem;
  color: rgba(255,255,255,0.15);
}
.empty-state p {
  color: rgba(255,255,255,0.5);
  font-size: 0.95rem;
  margin: 0;
}
.empty-state span {
  font-size: 0.75rem;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  color: #c9a96e;
  opacity: 0.6;
}

@media (max-width: 640px) {
  .projects-grid { grid-template-columns: 1fr; }
  .proj-item { grid-template-columns: 1fr; }
  .proj-item::before { display: none; }
  .proj-arrow { display: none; }
}
</style>
