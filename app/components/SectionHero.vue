<script setup lang="ts">

const whatsappNumber = '5527999720808' 
const whatsappMessage = 'Olá! Gostaria de agendar uma visita ao Quintas Dumonte.'
const whatsappLink = `https://wa.me/${whatsappNumber}?text=${encodeURIComponent(whatsappMessage)}`
/**
 * Componente: SectionHero - Versão Cores Diretas (Hardcoded)
 * Função: Primeira dobra do site. Deve impactar e resumir a proposta de valor.
 */
</script>

<template>
  <section class=" relative isolate rounded-t-[35px] overflow-hidden bg-[#101010] min-h-[calc(100vh-65px)] flex items-center">
    
    <img 
      src="/hero-sitio-terreno.jpg" 
      alt="Vista aérea da pedra azul" 
      class=" absolute top-[-80px] left-0 w-full h-[120%] -z-10 object-cover brightness-70"
      fetchpriority="high"
    />


    <div class="absolute inset-0 -z-10 bg-gradient-to-t from-[#101010]/80 via-[#101010]/40 to-transparent"></div>
    
    <div class=" mx-auto max-w-7xl px-6 lg:px-8 text-center flex flex-col justify-center items-center gap-6">
      
      <h1 class="text-[#CBBD93] text-6xl font-bold drop-shadow-[0_2px_6px_rgba(0,0,0,0.8)]">
        <span class="italic">Quintas</span> Dumonte
      </h1><br/>
      

      <h2 class="mx-auto ... text-white drop-shadow-[0_2px_6px_rgba(0,0,0,0.9)]">
        Sítio de lazer fechado e familiar.<br class="hidden sm:block" />
      </h2>

      <p class="mx-auto ... text-gray-300 drop-shadow-[0_2px_4px_rgba(0,0,0,0.8)]">
        Adquira sua chácara com facilidade, parcelamos em até <span class="font-semibold">60x</span><br/> <span class="italic text-sm text-[#CBBD93]">Confira as condições.</span>
      </p>


      <div class="mt-10 flex items-center justify-center gap-x-6">
        
        <a 
          :href="whatsappLink" 
          target="_blank"
          class="rounded-md bg-[#CBBD93] px-5 py-3 text-base font-semibold text-[#101010] shadow-sm hover:bg-[#E3D38B] focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-[#D8C67A] transition-all duration-300 transform hover:scale-105"
        >
          Entre em contato
        </a>

        <a href="#features" class="text-sm font-semibold leading-6 text-white hover:text-[#D8C67A] transition-colors flex items-center gap-1">
          Conhecer detalhes <span aria-hidden="true">→</span>
        </a>
      </div>

    </div>
  </section>
</template>

<style scoped>
/* Animação simples de entrada */
.animate-fade-in-up {
  animation: fadeInUp 0.8s ease-out forwards;
}

@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}
</style>