<template>
  <div id="app">
    <HeroSection
      :active-tab="activeTab"
      @open-tab="openTab"
    />

    <PortfolioModal
      :active-tab="activeTab"
      @close="closeTab"
    />
  </div>
</template>

<script>
import HeroSection    from './components/HeroSection.vue'
import PortfolioModal from './components/PortfolioModal.vue'
 
export default {
  name: 'App',
  components: {
    HeroSection,
    PortfolioModal
  },
  data() {
    return {
      activeTab: null
    }
  },
  methods: {
    openTab(tab) {
      this.activeTab = tab
    },
    closeTab() {
      this.activeTab = null
    }
  },
  mounted() {
    document.addEventListener('keydown', (e) => {
      if (e.key === 'Escape') this.closeTab()
    })
  },
  beforeUnmount() {
    document.removeEventListener('keydown', this.closeTab)
  }
}
</script>
