<script setup lang="ts">
/**
 * Componente: Header (Cabeçalho)
 * Função: Navegação principal e CTA.
 * Comportamento: Fixo no topo, ganha borda ao rolar.
 */

// Estado para controlar o menu mobile
const isMenuOpen = ref(false)
// Estado para controlar se a página foi rolada
const isScrolled = ref(false)

const closeMenu = () => {
  isMenuOpen.value = false
}

// Monitorar o Scroll para adicionar a borda
const handleScroll = () => {
  isScrolled.value = window.scrollY > 10 // Se desceu mais de 10px, ativa a borda
}

onMounted(() => {
  window.addEventListener('scroll', handleScroll)
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
})

const whatsappNumber = '5527999720808' 
const whatsappMessage = 'Olá! Gostaria de agendar uma visita ao Quintas Dumonte.'
const whatsappLink = `https://wa.me/${whatsappNumber}?text=${encodeURIComponent(whatsappMessage)}`

const navLinks = [
  { label: 'O Refúgio', hash: '#intro' },
  { label: 'Nossa hitória', hash: '#features' },
  { label: 'Localização', hash: '#location' },
  { label: 'Galeria', hash: '#gallery' },
  { label: 'Terrenos', hash: '#lots' },
]
</script>

<template>
  <!-- 
    Header Dinâmico:
    - :class controla a borda baseado em isScrolled.
    - border-transparent: Sem borda no topo.
    - border-b border-gray-200: Com borda ao rolar.
  -->
  <header 
    :class="[
      'sticky top-0 z-50 w-full bg-white/90 backdrop-blur-md transition-all duration-300',
      isScrolled ? 'border-b border-gray-200 shadow-sm' : 'border-b border-transparent'
    ]"
  >
    
    <div class="mx-auto flex h-16 max-w-7xl items-center justify-between px-4 sm:px-6 lg:px-8">
      
      <!-- LOGO -->
      <div class="flex items-center -ml-3">
        <a href="#">
          <NuxtImg src="/quintas2.png" width="150" alt="Quintas Dumonte" />
        </a>
      </div>

      <!-- NAVEGAÇÃO DESKTOP -->
      <nav class="hidden md:flex items-center gap-8">
        <a 
          v-for="link in navLinks" 
          :key="link.hash" 
          :href="link.hash"
          class="text-md font-medium text-gray-700 hover:text-[#CBBD93] transition-colors"
        >
          {{ link.label }}
        </a>
      </nav>

      <!-- CTA DESKTOP -->
      <div class="hidden md:flex">
        <a :href="whatsappLink" target="_blank" class="rounded-md bg-[#CBBD93] px-5 py-3 text-base font-semibold text-[#101010] shadow-sm hover:bg-[#E3D38B] focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-[#D8C67A] transition-all duration-300 transform hover:scale-105">
          Agendar visita
        </a>
      </div>

      <!-- BOTÃO MENU MOBILE -->
      <div class="flex md:hidden">
        <button 
          @click="isMenuOpen = !isMenuOpen"
          aria-label="Abrir menu principal"
          class="text-[#101010] focus:outline-none"
        >
          <UIcon 
            :name="isMenuOpen ? 'i-heroicons-x-mark' : 'i-heroicons-bars-3'" 
            class="h-7 w-7" 
          />
        </button>
      </div>
    </div>

    <!-- MENU MOBILE -->
    <Transition
      enter-active-class="transition duration-200 ease-out"
      enter-from-class="transform -translate-y-5 opacity-0"
      enter-to-class="transform translate-y-0 opacity-100"
      leave-active-class="transition duration-150 ease-in"
      leave-from-class="transform translate-y-0 opacity-100"
      leave-to-class="transform -translate-y-5 opacity-0"
    >
      <div v-if="isMenuOpen" class="md:hidden border-t border-gray-100 bg-white absolute w-full shadow-lg">
        <div class="space-y-1 px-4 py-6">
          <a 
            v-for="link in navLinks" 
            :key="link.hash" 
            :href="link.hash"
            class="block border-l-4 border-transparent py-3 pl-3 text-base font-medium text-gray-600 hover:border-[#D8C67A] hover:bg-gray-50 hover:text-[#101010]"
            @click="closeMenu"
          >
            {{ link.label }}
          </a>
          
          <div class="mt-6 pt-4 border-t border-gray-100">
            <a 
              href="#contact" 
              class="flex w-full items-center justify-center rounded-md bg-[#CBBD93] px-4 py-3 text-base font-bold text-gray-800 hover:bg-[#D8C67A] transition-colors"
              @click="closeMenu"
            >
              Agendar visita
            </a>
          </div>
        </div>
      </div>
    </Transition>

  </header>
</template>