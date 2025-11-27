<script setup lang="ts">
/**
 * Componente: SectionLots (Terrenos à Venda - Estilo Carrossel Responsivo)
 * Funcionalidade: Slider que mostra 1, 2 ou 3 cards dependendo da tela.
 */

// Referência para o scroll e estado ativo
const scrollContainer = ref<HTMLElement | null>(null)
const activeIndex = ref(0)
const showControls = ref(true) // Controla visibilidade de setas/bolinhas
const itemsPerPage = ref(1) // Quantos itens cabem na tela agora

const whatsappNumber = '5527999720808' 
const whatsappMessage = 'Olá! Gostaria de saber mais informações sobre os terrenos.'
const whatsappLink = `https://wa.me/${whatsappNumber}?text=${encodeURIComponent(whatsappMessage)}`

const lots = [
  {
    id: 1,
    title: 'Chácara A',
    area: '1.678 m²',
    description: 'Com platô, área gramada, pomar formado, água disponível e ligação de energia pela EDP.',
    image: '/terreno-1678.jpg',
    status: 'Pronto para construir'
  },
  {
    id: 2,
    title: 'Chácara B',
    area: '1.443 m²',
    description: 'O terreno possui platô pronto, água instalada, luz disponível e área gramada.',
    image: '/terreno-1443.jpg',
    status: 'Pronto para construir'
  },
  {
    id: 3,
    title: 'Chácara C',
    area: '1.000 m²',
    description: 'Situado ao lado de uma bela área de mata, garantindo privacidade e contato direto com a natureza.',
    image: '/terreno-1000-mata.jpg',
    status: 'Disponível'
  },
   {
    id: 3,
    title: 'Chácara C',
    area: '1.000 m²',
    description: 'Situado ao lado de uma bela área de mata, garantindo privacidade e contato direto com a natureza.',
    image: '/terreno-1000-mata.jpg',
    status: 'Disponível'
  },
  // Adicione mais lotes aqui...
]

// Função de Scroll Dinâmica (Setas)
const scroll = (direction: 'left' | 'right') => {
  if (!scrollContainer.value) return
  
  const firstCard = scrollContainer.value.querySelector('.snap-center') as HTMLElement | null
  const cardWidth = firstCard ? firstCard.offsetWidth : 300
  const gap = 24 
  
  // Rola a largura de uma "página" ou um card
  const scrollAmount = cardWidth + gap
  
  scrollContainer.value.scrollBy({
    left: direction === 'left' ? -scrollAmount : scrollAmount,
    behavior: 'smooth'
  })
}

// Função para rolar ao clicar na bolinha (Página)
const scrollToPage = (pageIndex: number) => {
  if (!scrollContainer.value) return
  const container = scrollContainer.value
  const children = Array.from(container.children) as HTMLElement[]
  const cards = children.filter(child => child.classList.contains('group'))
  
  // Calcula o índice do primeiro item da página alvo
  const targetItemIndex = pageIndex * itemsPerPage.value
  
  if (cards[targetItemIndex]) {
    cards[targetItemIndex].scrollIntoView({ 
      behavior: 'smooth', 
      block: 'nearest', 
      inline: window.innerWidth < 768 ? 'center' : 'start'
    })
  }
}

// Função para detectar item visível e atualizar paginação
const onScroll = () => {
  if (!scrollContainer.value) return
  const container = scrollContainer.value
  const center = container.scrollLeft + container.clientWidth / 2
  
  // Lógica para detectar fim do scroll (ativar última bolinha)
  if (container.scrollLeft + container.clientWidth >= container.scrollWidth - 10) {
     activeIndex.value = lots.length - 1
     return
  }

  const children = Array.from(container.children) as HTMLElement[]
  const lotCards = children.filter(child => child.classList.contains('group'))
  
  let closestIndex = 0
  let minDistance = Infinity

  lotCards.forEach((child, index) => {
    const childPoint = window.innerWidth < 768 
      ? child.offsetLeft + child.offsetWidth / 2 
      : child.offsetLeft
      
    const referencePoint = window.innerWidth < 768 ? center : container.scrollLeft
    
    const distance = Math.abs(childPoint - referencePoint)
    
    if (distance < minDistance) {
      minDistance = distance
      closestIndex = index
    }
  })
  
  activeIndex.value = closestIndex
}

// Atualiza layout e paginação baseado na tela
const updateLayout = () => {
  if (!scrollContainer.value) return
  
  // Definir itens por página
  if (window.innerWidth >= 1024) {
    itemsPerPage.value = 3
  } else if (window.innerWidth >= 768) {
    itemsPerPage.value = 2
  } else {
    itemsPerPage.value = 1
  }

  // Verificar se precisa de controles
  showControls.value = scrollContainer.value.scrollWidth > (scrollContainer.value.clientWidth + 1)
}

onMounted(() => {
  updateLayout()
  window.addEventListener('resize', updateLayout)
})

onUnmounted(() => {
  window.removeEventListener('resize', updateLayout)
})

const getStatusColor = (status: string) => {
  if (status === 'Última Unidade') return 'bg-red-100 text-red-700 ring-red-600/20'
  if (status === 'Reservado') return 'bg-gray-100 text-gray-600 ring-gray-500/10'
  return 'bg-[#28A745] text-white ring-[#28A745]/50 shadow-sm'
}
</script>

<template>
  <section class="py-16 bg-white overflow-hidden" id="lots">
    <div class="mx-auto max-w-7xl px-6 lg:px-8">
      
      <!-- CABEÇALHO -->
      <div class="mx-auto max-w-2xl text-center">
        <h2 class="text-base font-semibold leading-7 text-[#81785d] uppercase tracking-wide">
          Disponibilidade
        </h2>
        <h3 class="mt-2 mb-6 text-2xl font-bold tracking-tight text-[#101010] sm:text-4xl">
          Invista na sua qualidade de vida
        </h3>
      </div>

      <!-- CONTAINER RELATIVO -->
      <div class="relative group/carousel">
        
        <!-- BOTÃO ANTERIOR (Ajustado para a borda exata) -->
        <button 
          v-if="showControls"
          @click="scroll('left')"
          class="cursor-pointer flex md:flex absolute -left-1 top-1/2 -translate-y-1/2 z-10 bg-transparent backdrop-blur-sm border border-gray-200 p-3 rounded-full shadow-lg text-gray-600 md:hover:bg-[#D8C67A] md:hover:text-white md:hover:border-[#D8C67A] transition-all transform hover:scale-110 -ml-4 lg:-ml-6"
          aria-label="Anterior"
        >
          <UIcon name="i-heroicons-chevron-left" class="w-6 h-6" />
        </button>

        <!-- CARROSSEL -->
        <div 
          ref="scrollContainer"
          @scroll.passive="onScroll"
          class="flex gap-6 overflow-x-auto pb-2 pt-4 snap-x snap-mandatory scrollbar-hide px-1"
        >
          <div 
            v-for="lot in lots" 
            :key="lot.id" 
            class="
              group flex flex-col rounded-2xl bg-white border border-gray-100 shadow-sm hover:shadow-xl transition-all duration-300 hover:-translate-y-1 h-130 shrink-0
              snap-center md:snap-start
              w-full 
              md:w-[calc(50%-12px)] 
              lg:w-[calc(33.333%-16px)]
            "
          >
            <!-- IMAGEM DO LOTE -->
            <div class="relative h-60 overflow-hidden rounded-t-2xl bg-gray-100">
              <img 
                :src="lot.image" 
                :alt="lot.title"
                loading="lazy" 
                class="h-full w-full object-cover transition-transform duration-500 group-hover:scale-110"
              />
              <div class="absolute top-4 right-4">
                <span 
                  :class="['inline-flex items-center rounded-full px-3 py-1 text-xs font-bold ring-1 ring-inset uppercase tracking-wide', getStatusColor(lot.status)]"
                >
                  {{ lot.status }}
                </span>
              </div>
            </div>

            <!-- CONTEÚDO -->
            <div class="flex flex-1 flex-col p-6">
              <h3 class="text-xl font-bold text-[#101010]">
                {{ lot.title }}
              </h3>
              <div class="mt-3 flex items-center gap-2 text-sm font-medium text-gray-500 pb-4 border-b border-gray-100">
                <UIcon name="i-heroicons-arrows-pointing-out" class="h-5 w-5 text-[#81785d]" />
                <span>{{ lot.area }}</span>
              </div>
              <p class="mt-4 text-sm leading-relaxed text-gray-600 flex-grow line-clamp-3">
                {{ lot.description }}
              </p>
              <div class="pt-2">
                <a 
                  :href="whatsappLink" 
                  target="_blank"
                  class="flex w-full items-center justify-center gap-2 rounded-lg border border-[#101010] px-4 py-3 text-sm font-bold text-[#101010] hover:bg-[#101010] hover:text-white transition-all duration-300"
                >
                  <span>Consultar valor</span>
                  <UIcon name="i-heroicons-arrow-right" class="w-4 h-4" />
                </a>
              </div>
            </div>
          </div>
        </div>

        <!-- BOTÃO PRÓXIMO (Ajustado para a borda exata) -->
        <button 
          v-if="showControls"
          @click="scroll('right')"
          class="cursor-pointer flex md:flex absolute -right-1 top-1/2 -translate-y-1/2 z-10 bg-transparent backdrop-blur-sm border border-gray-200 p-3 rounded-full shadow-lg text-gray-600 md:hover:bg-[#CBBD93] md:hover:text-white md:hover:border-[#CBBD93] transition-all transform md-hover:scale-110 -mr-4 lg:-mr-6"
          aria-label="Próximo"
        >
          <UIcon name="i-heroicons-chevron-right" class="w-6 h-6" />
        </button>

      </div>

      <!-- INDICADORES DE PÁGINA (BOLINHAS) -->
      <div v-if="showControls" class="flex justify-center items-center gap-2 mt-4 flex-wrap px-4">
        <!-- Loop baseado no número total de PÁGINAS (Math.ceil) -->
        <button 
          v-for="pageIndex in Math.ceil(lots.length / itemsPerPage)" 
          :key="pageIndex"
          @click="scrollToPage(pageIndex - 1)"
          :class="[
            'rounded-full transition-all duration-300',
            // Verifica se a página atual corresponde ao item ativo
            Math.floor(activeIndex / itemsPerPage) === pageIndex - 1
              ? 'bg-[#81785d] w-10 h-2.5' 
              : 'bg-gray-300 w-2.5 h-2.5 hover:bg-gray-400'
          ]"
          :aria-label="`Ir para página ${pageIndex}`"
        />
      </div>

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