<template>
  <div>
    <h2 class="modal-title">Experiência Profissional</h2>

    <div class="exp-list">
      <div v-for="(exp, index) in experiencias" :key="exp.empresa" class="exp-item"
        :class="{ 'last': index === experiencias.length - 1 }">
        <div class="exp-company">{{ exp.empresa }}</div>
        <div>
          <p class="exp-desc">{{ exp.descricao }}</p>
          <div class="tag-list">
            <span v-for="tag in exp.tags" :key="tag" class="tag">{{ tag }}</span>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ModalExperiencia',
  data() {
    return {
      experiencias: [
        {
          empresa: 'USJT',
          descricao: 'Ajudava os alunos nas listas de exercícios das disciplinas de Algoritmo e Estrutura de Dados em Java e MySQL, atuando como monitor.',
          tags: ['Java', 'MySQL', 'Algoritmos', 'Estrutura de Dados']
        },
        {
          empresa: 'Bom Valor',
          descricao: 'Responsável pela migração do frontend de uma aplicação Django para Vue.js com Bootstrap, integrando com PostgreSQL e Docker, seguindo Scrum.',
          tags: ['Vue.js', 'Bootstrap', 'PostgreSQL', 'Docker', 'Scrum']
        },
        {
          empresa: 'Influu',
          descricao: 'Trabalhei com RPA e utilizei Vue ou React, dependendo do projeto, ambos integrados com NodeJS e PostgreSQL como banco de dados.',
          tags: ['RPA', 'Vue.js', 'React', 'NodeJS', 'PostgreSQL']
        },
        {
          empresa: 'Braxxy',
          descricao: 'Trabalhei com Spring Boot, Vue, Redis, PostgreSQL e MongoDB em projetos de alta escala.',
          tags: ['Spring Boot', 'Vue.js', 'Redis', 'PostgreSQL', 'MongoDB']
        },
        {
          empresa: 'WeVets',
          descricao: 'Atuação na plataforma Sydle com foco em otimização de processos, gestão de fluxos e demandas, utilizando CRM e Sydle UI para ganho de eficiência operacional.',
          tags: ['Sydle', 'CRM', 'BPM', 'Sydle UI']
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

.exp-list {
  display: flex;
  flex-direction: column;
}

.exp-item {
  display: grid;
  grid-template-columns: 160px 1fr;
  gap: 24px;
  padding: 24px 0;
  border-bottom: 1px solid rgba(255, 255, 255, 0.07);
  position: relative;
}

.exp-item::before {
  content: '';
  position: absolute;
  left: 150px;
  top: 0;
  bottom: 0;
  width: 1px;
  background: rgba(255, 255, 255, 0.07);
}

.exp-item.last {
  border-bottom: none;
}

.exp-company {
  font-family: 'Cormorant Garamond', serif;
  font-size: 1.05rem;
  font-weight: 600;
  color: #c9a96e;
  letter-spacing: 0.04em;
  padding-right: 16px;
}

.exp-desc {
  font-size: 0.9rem;
  line-height: 1.75;
  color: rgba(255, 255, 255, 0.75);
  font-weight: 300;
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
  border: 1px solid rgba(255, 255, 255, 0.15);
  border-radius: 20px;
  color: rgba(255, 255, 255, 0.55);
  letter-spacing: 0.05em;
}

@media (max-width: 640px) {
  .exp-item {
    grid-template-columns: 1fr;
  }

  .exp-item::before {
    display: none;
  }
}
</style>
