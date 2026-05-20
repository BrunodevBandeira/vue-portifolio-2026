<template>
  <div>
    <h2 class="modal-title">Sobre Mim</h2>
    <p class="sobre-text">
      Sou Desenvolvedor Full Stack Java com 2+ anos de experiência, com formação em Engenharia da
      Computação e especialização por meio de bootcamps como Generation Brasil, IGTI e Digital
      Innovation One. Atuo no desenvolvimento de aplicações completas, do backend ao frontend,
      utilizando tecnologias como Spring Boot, Vue.js, React e bancos de dados relacionais e não
      relacionais. Tenho experiência em criação de interfaces responsivas, integração de sistemas,
      automação de processos (RPA) e utilização de mensageria com RabbitMQ, sempre seguindo
      metodologias ágeis como Scrum e Kanban. Também atuei como monitor de algoritmos e estruturas
      de dados, fortalecendo minha base lógica e capacidade de resolução de problemas. Atualmente,
      foco na otimização de processos e uso de plataformas como Sydle, com forte orientação à
      eficiência operacional, qualidade de entrega e evolução contínua.
    </p>
  </div>
</template>

<script>
export default {
  name: 'ModalSobre'
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

.sobre-text {
  font-size: 1rem;
  line-height: 1.9;
  color: rgba(255, 255, 255, 0.82);
  font-weight: 300;
}
</style>
