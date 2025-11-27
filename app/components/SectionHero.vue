<script setup lang="ts">

const whatsappNumber = '5527999720808' 
const whatsappMessage = 'Olá! Gostaria de saber mais informações.'
const whatsappLink = `https://wa.me/${whatsappNumber}?text=${encodeURIComponent(whatsappMessage)}`
/**
 * Componente: SectionHero - Versão Cores Diretas (Hardcoded)
 * Função: Primeira dobra do site. Deve impactar e resumir a proposta de valor.
 */
</script>

<template>
  <section class="relative isolate overflow-hidden bg-[#101010] min-h-[calc(100vh-65px)] flex items-center">
    
    <img 
      src="/hero-sitio-terreno.jpg" 
      alt="Vista aérea da pedra azul" 
      class=" absolute top-[-80px] left-0 w-full h-[120%] -z-10 object-cover brightness-70"
      fetchpriority="high"
    />


    <div class="absolute inset-0 -z-10 bg-gradient-to-t from-[#101010]/40 via-[#101010]/30 to-transparent"></div>
    
    <div class="-mt-15 mx-auto max-w-7xl px-5 lg:px-8 h-150 text-center flex flex-col justify-center items-center gap-32">
      
        <h1 class="font-serif text-[#CBBD93] text-[2.4rem] font-bold drop-shadow-[0_2px_6px_rgba(0,0,0,0.8)]">
          Sítio de lazer fechado e familiar.
        </h1>

        <p class="mx-auto ... text-xl  text-gray-300 drop-shadow-[0_2px_4px_rgba(0,0,0,0.8)]">
          Adquira sua chácara com facilidade, parcelamos em até <span class="font-semibold">60x</span><br/>
        </p>


      <div class=" flex items-center justify-center gap-x-6">
        <a href="#lots" class="text-sm font-semibold leading-6 text-white hover:text-[#D8C67A] transition-colors flex items-center gap-1">
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