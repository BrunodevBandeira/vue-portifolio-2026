<template>
  <transition name="fade">
    <div
      v-if="activeTab"
      class="modal-overlay"
      @click.self="$emit('close')"
    >
      <div class="modal">
        <button class="modal-close" @click="$emit('close')">
          <i class="fas fa-times"></i>
        </button>

        <ModalSobre       v-if="activeTab === 'sobre'" />
        <ModalContato     v-if="activeTab === 'contato'" />
        <ModalProjetos    v-if="activeTab === 'projetos'" />
        <ModalExperiencia v-if="activeTab === 'experiencia'" />
      </div>
    </div>
  </transition>
</template>

<script>
import ModalSobre       from './ModalSobre.vue'
import ModalContato     from './ModalContato.vue'
import ModalProjetos    from './ModalProjetos.vue'
import ModalExperiencia from './ModalExperiencia.vue'

export default {
  name: 'PortfolioModal',
  components: {
    ModalSobre,
    ModalContato,
    ModalProjetos,
    ModalExperiencia
  },
  emits: ['close'],
  props: {
    activeTab: {
      type: String,
      default: null
    }
  }
}
</script>

<style scoped>
.modal-overlay {
  position: fixed;
  inset: 0;
  background: rgba(0, 0, 0, 0.75);
  backdrop-filter: blur(6px);
  z-index: 100;
  display: flex;
  align-items: center;
  justify-content: center;
}

.modal {
  background: linear-gradient(135deg, rgba(15,15,18,0.97) 0%, rgba(22,22,28,0.97) 100%);
  border: 1px solid rgba(255, 255, 255, 0.1);
  border-radius: 12px;
  padding: 48px;
  width: min(900px, 92vw);
  max-height: 88vh;
  overflow-y: auto;
  position: relative;
  animation: slideUp 0.4s cubic-bezier(0.4, 0, 0.2, 1);
  scrollbar-width: thin;
  scrollbar-color: rgba(255,255,255,0.2) transparent;
}

@keyframes slideUp {
  from { opacity: 0; transform: translateY(30px); }
  to   { opacity: 1; transform: translateY(0);    }
}

.modal-close {
  position: absolute;
  top: 18px;
  right: 22px;
  background: none;
  border: none;
  color: rgba(255, 255, 255, 0.5);
  font-size: 1.5rem;
  cursor: pointer;
  transition: color 0.2s;
}
.modal-close:hover { color: #fff; }

/* Transition fade */
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.3s ease;
}
.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}

@media (max-width: 640px) {
  .modal { padding: 32px 24px; }
}
</style>
