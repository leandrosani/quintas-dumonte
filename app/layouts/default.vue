<script setup lang="ts">
/**
 * Layout Principal - Quintas Dumonte
 * -----------------------------------------------------------------
 * Define a estrutura base: Header fixo ou não, Área de conteúdo e Footer.
 * Responsável pela tipografia global e comportamento de rolagem.
 */

// Configuração de meta tags básicas para SEO e UX (scroll suave)
useHead({
  htmlAttrs: {
    class: 'scroll-smooth' // Permite a navegação suave entre as seções (#âncoras)
  },
  titleTemplate: (titleChunk) => {
    return titleChunk ? `${titleChunk} - Quintas Dumonte` : 'Quintas Dumonte';
  }
})
</script>

<template>
  <div class="min-h-screen flex flex-col font-sans antialiased bg-gray-50 text-gray-900 selection:bg-brand-sand selection:text-brand-black">
    
    <AppHeader />

    <main class="flex-grow w-full">
      <slot />
    </main>

    <AppFooter />
    <WhatsAppButton />
  </div>
</template>

<style scoped>
/* Se precisar de ajustes globais muito específicos, use aqui.
  Por enquanto, manteremos vazio para confiar 100% no Tailwind.
*/
</style>