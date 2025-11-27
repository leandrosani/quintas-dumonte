<script setup lang="ts">
/**
 * Componente: SectionGallery (Estrutura de Lazer)
 * Estilo: Carrossel horizontal (Slider) com fundo claro e cards ULTRA GIGANTES.
 * Funcionalidade: Scroll suave, dicas visuais e indicadores de paginação.
 */

// Referência para o container do scroll
const scrollContainer = ref<HTMLElement | null>(null)
// Estado para saber qual slide está ativo (0 = primeiro)
const activeIndex = ref(0)

// Lista completa atualizada
const photos = [
  {
    title: 'Lagoas',
    description: 'Lagoas naturais com pesque e solte.',
    src: '/lagoa-7anoes.jpg'
  },
  {
    title: 'Área de Festas',
    description: 'Espaço amplo e equipado para celebrar momentos especiais com a família. Com som, karaoke...',
    src: '/area-festa.jpg'
  },
  {
    title: 'Lareira Interna',
    description: 'O charme do fogo suspenso para as noites frias e conversas longas.',
    src: '/lareira-festa.jpg'
  },
  {
    title: 'Suítes',
    description: 'Suítes confortáveis para passar os seus finais de semana.',
    src: '/pousada1.jpg'
  },
  {
    title: 'Campo de Futebol',
    description: 'Gramado natural para jogar futebol.',
    src: '/campo-futebol.jpg'
  },
  {
    title: 'Relaxar',
    description: 'Relaxar no embalo de uma rede num clima agradável.',
    src: '/lazer-relaxar.jpg'
  },
  {
    title: 'Lareira Externa',
    description: 'Queimar um marshmallow e tomar um vinho/suco na lareira.',
    src: '/lazer-lareira-externa.jpg'
  },
  {
    title: 'Parquinho',
    description: 'Parquinho para as crianças brincarem.',
    src: '/lazer-parquinho.jpg'
  },
  {
    title: 'Arco-íris',
    description: 'Arco-íris, nossa aliança.',
    src: '/sitio-arcoires.jpg'
  },
  {
    title: 'Entardecer',
    description: 'Entardecer perfeito.',
    src: '/sitio-entardecer.jpg'
  }
]

// Função para rolar com as setas (Desktop)
const scroll = (direction: 'left' | 'right') => {
  if (!scrollContainer.value) return
  
  // AJUSTE: Largura do card (1000px) + Gap (24px) = 1024
  const scrollAmount = 1024 
  
  scrollContainer.value.scrollBy({
    left: direction === 'left' ? -scrollAmount : scrollAmount,
    behavior: 'smooth'
  })
}

// Função para rolar ao clicar na bolinha
const scrollToIndex = (index: number) => {
  if (!scrollContainer.value) return
  const container = scrollContainer.value
  const children = Array.from(container.children) as HTMLElement[]
  
  if (children[index]) {
    children[index].scrollIntoView({ 
      behavior: 'smooth', 
      block: 'nearest', 
      inline: 'center' 
    })
  }
}

// Função para detectar qual slide está visível durante o scroll
const onScroll = () => {
  if (!scrollContainer.value) return
  const container = scrollContainer.value
  const center = container.scrollLeft + container.clientWidth / 2
  
  const children = Array.from(container.children) as HTMLElement[]
  const photoCards = children.slice(0, photos.length)
  
  let closestIndex = 0
  let minDistance = Infinity

  photoCards.forEach((child, index) => {
    const childCenter = child.offsetLeft + child.offsetWidth / 2
    const distance = Math.abs(childCenter - center)
    
    if (distance < minDistance) {
      minDistance = distance
      closestIndex = index
    }
  })
  
  activeIndex.value = closestIndex
}
</script>

<template>
  <section class="py-16 bg-gradient-to-r from-white via-[#f7f4e4d3] to-white text-gray-900 overflow-hidden relative isolate" id="gallery">
    <div class="mx-auto max-w-7xl px-6 lg:px-8">
      
      <div class="flex flex-col md:flex-row md:items-end justify-between gap-6 mb-2">
        <div class="max-w-2xl">
          <h2 class="text-base font-semibold leading-7 text-[#81785d] uppercase tracking-wide">
            Lazer e Conforto
          </h2>
          <h3 class="mt-2 text-2xl font-bold tracking-tight text-gray-800 sm:text-4xl">
            Estrutura pronta para você aproveitar
          </h3>
          <p class="mt-4 text-gray-600">
            Além do seu terreno, o Quintas Dumonte oferece áreas comuns pensadas para o bem-estar coletivo e familiar.
          </p>
          
          <div class="flex items-center justify-between pt-8">
            <h3 class="text-black font-bold text-base">GALERIA</h3>
            
            <!-- DICA VISUAL MOBILE -->
            <div class="md:hidden flex items-center gap-2 text-sm text-[#81785d] font-medium animate-pulse">
              <span>Deslize</span>
              <UIcon name="i-heroicons-arrow-right" class="w-4 h-4" />
            </div>
          </div>
        </div>

        <!-- Botões Desktop -->
        <div class="hidden md:flex gap-4">
          <button 
            @click="scroll('left')"
            aria-label="Foto anterior"
            class="cursor-pointer rounded-full border border-gray-700 p-3 hover:bg-[#CBBD93] hover:border-[#CBBD93] text-black hover:text-[#101010] transition-all flex justify-center items-center h-12 w-12"
          >
            <UIcon name="i-heroicons-chevron-left" class="w-6 h-6" />
          </button>
          <button 
            @click="scroll('right')"
            aria-label="Próxima foto"
            class="cursor-pointer rounded-full border border-gray-700 p-3 hover:bg-[#CBBD93] hover:border-[#CBBD93] text-black hover:text-[#101010] transition-all flex justify-center items-center h-12 w-12"
          >
            <UIcon name="i-heroicons-chevron-right" class="w-6 h-6" />
          </button>
        </div>
      </div>
    </div>
    <!-- CARROSSEL -->
      <div 
        ref="scrollContainer"
        @scroll.passive="onScroll"
        class="flex gap-6 overflow-x-auto pb-8 snap-x snap-mandatory scrollbar-hide"
      >
        <div 
          v-for="(photo, index) in photos" 
          :key="index"
          class="snap-center snap-always shrink-0 w-screen md:w-[1000px] group relative overflow-hidden shadow-xl"
        >
          <!-- 
             UPGRADE DE TAMANHO ULTRA:
             - Mobile: w-[90vw] (Quase tela cheia)
             - Desktop: w-[1000px] (Massivo)
          -->
          <div class="aspect-[3/3] md:aspect-[16/9] w-full overflow-hidden">
            <img 
              :src="photo.src" 
              :alt="photo.title" 
              loading="lazy"
              class="h-full w-full object-cover"
            />
          </div>
          
          <div class="absolute inset-0 bg-gradient-to-t from-black/60 via-black/20 to-transparent"></div>

          <div class="absolute bottom-0 left-0 p-6 md:p-10">
            <h3 class="text-xl md:text-4xl font-bold text-white mb-2 drop-shadow-md">
              {{ photo.title }}
            </h3>
            <p class="text-sm md:text-xl text-gray-200 leading-relaxed max-w-2xl">
              {{ photo.description }}
            </p>
          </div>
        </div>
        
        <!-- Espaçador final -->
        <div class="shrink-0 w-6 md:w-0"></div>
      </div>

      <!-- INDICADORES (BOLINHAS) -->
      <div class="flex justify-center items-center gap-2 mt-6 flex-wrap px-4">
        <button 
          v-for="(_, index) in photos" 
          :key="index"
          @click="scrollToIndex(index)"
          :class="[
            'rounded-full transition-all duration-300',
            index === activeIndex 
              ? 'bg-[#81785d] w-10 h-2.5' // Um pouco maior para acompanhar a escala
              : 'bg-gray-300 w-2.5 h-2.5 hover:bg-gray-400'
          ]"
          :aria-label="`Ir para foto ${index + 1}`"
        />
      </div>
  </section>
</template>

<style scoped>
.scrollbar-hide::-webkit-scrollbar {
    display: none;
}
.scrollbar-hide {
    -ms-overflow-style: none;
    scrollbar-width: none;
}
</style>