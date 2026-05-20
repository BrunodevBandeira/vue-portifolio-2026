<template>
  <div>
    <h2 class="modal-title">Contato</h2>
    <div class="contato-grid">

      <!-- ESQUERDA -->
      <div class="contato-left">
        <h3>Meus Contatos!</h3>
        <p>Em busca de desenvolvimento e experiência :)</p>
        <p>Quem sabe na sua empresa?</p>
        <p class="email-label">
          Estou disponível para bater um papo, você pode entrar em contato via e-mail:
        </p>
        <p>
          <a href="mailto:brunobandeira25ab@gmail.com">brunobandeira25ab@gmail.com</a>
        </p>

        <div class="social-icons">
          <a
            class="social-icon"
            href="https://www.linkedin.com/in/brunodevbandeira"
            target="_blank"
            rel="noopener noreferrer"
          >
            <i class="fab fa-linkedin"></i> LinkedIn
          </a>
          <a
            class="social-icon"
            href="https://github.com/DevBrunoBandeira"
            target="_blank"
            rel="noopener noreferrer"
          >
            <i class="fab fa-github"></i> GitHub
          </a>
        </div>
      </div>

      <!-- DIREITA -->
      <div class="contato-right">
        <img
          class="contato-gif"
          src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExcWJvNHhudGhxMnlpbDk1aXhpOHBqeXBzMjl6bm9mMDU0bHBuNmZ3ZyZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/qgQUggAC3Pfv687qPC/giphy.gif"
          alt="Entre em contato"
        />
      </div>

    </div>
  </div>
</template>

<script>
export default {
  name: 'ModalContato'
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

.contato-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 40px;
  align-items: center;
}

.contato-left h3 {
  font-family: 'Cormorant Garamond', serif;
  font-size: 1.7rem;
  margin-bottom: 10px;
  color: #fff;
}

.contato-left p {
  color: rgba(255, 255, 255, 0.7);
  font-size: 0.9rem;
  line-height: 1.7;
  margin-bottom: 8px;
}

.email-label {
  margin-top: 16px !important;
}

.contato-left a {
  color: #c9a96e;
  text-decoration: none;
  transition: opacity 0.2s;
}
.contato-left a:hover { opacity: 0.75; }

.social-icons {
  display: flex;
  gap: 16px;
  margin-top: 24px;
  flex-wrap: wrap;
}

.social-icon {
  display: flex;
  align-items: center;
  gap: 8px;
  padding: 10px 20px;
  border: 1px solid rgba(255, 255, 255, 0.2);
  border-radius: 6px;
  color: #fff;
  text-decoration: none;
  font-size: 0.85rem;
  transition: background 0.2s, border-color 0.2s;
}
.social-icon:hover {
  background: rgba(255, 255, 255, 0.1);
  border-color: rgba(255, 255, 255, 0.5);
}
.social-icon i { font-size: 1.1rem; }

.contato-right {
  display: flex;
  align-items: center;
  justify-content: center;
}

.contato-gif {
  width: 100%;
  max-width: 320px;
  border-radius: 12px;
  object-fit: cover;
}

@media (max-width: 640px) {
  .contato-grid { grid-template-columns: 1fr; }
}
</style>
