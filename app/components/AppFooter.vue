<script setup lang="ts">

const navLinks = [
  { label: 'O Refúgio', hash: '#' },
  { label: 'Localização', hash: '#location' },
  { label: 'Galeria', hash: '#gallery' },
  { label: 'Terrenos', hash: '#lots' },
  { label: 'Nossa hitória', hash: '#features' },
]
/**
 * Componente: Footer (Rodapé)
 * Função: Informações finais, links rápidos e reforço de marca.
 * Estilo: Fundo escuro para contraste e elegância ("Dark Mode" local).
 */

// Pega o ano atual automaticamente (ex: 2025)
const currentYear = new Date().getFullYear()
</script>

<template>
  <footer class="text-gray-600 py-12 border-gray-800">
    <div class="mx-auto max-w-7xl px-4 sm:px-6 lg:px-8">
      
      <div class="grid grid-cols-1 gap-8 md:grid-cols-3">
        
        <div class="space-y-4">
          <a href="#">
            <img src="/quintas2.png" alt="Quintas Dumonte" width="200">
          </a>
          <p class="text-sm leading-relaxed max-w-xs">
            Sítio de lazer fechado e familiar
          </p>
        </div>

        <div class="space-y-4">
          <h4 class="text-sm font-semibold text-black uppercase tracking-wider">Explorar</h4>
          <nav>
            <ul class="">
              <li v-for="link in navLinks" :key="link.hash">
                <a :href="link.hash">
                  {{ link.label }}
                </a>
              </li>
            </ul>
          </nav>
        </div>
        
        <div class="space-y-4">
          <h4 class="text-sm font-semibold text-black uppercase tracking-wider">Contato</h4>
          <div class="space-y-2 text-sm">
            <p class="flex items-center gap-2">
              <UIcon name="i-heroicons-chat-bubble-left-right" class="w-5 h-5 text-[#81785d]" />
              <span>(27) 99972-0808</span>
            </p>
          </div>
        </div>
      </div>

      <div class="mt-12 border-t border-gray-800 pt-8 flex flex-col md:flex-row justify-between items-center gap-4 text-xs text-gray-500">
        
        <p>&copy; {{ currentYear }} Quintas Dumonte. Todos os direitos reservados.</p>
        
        <p class="flex items-center gap-2">
          Desenvolvido por 
          <a 
            href="https://landing-page.emeraldevs.workers.dev/" 
            target="_blank" 
            class="font-semibold text-[#02a871] hover:text-[#00ffaa] transition-colors flex justify-center items-center"
            
          >
            <img src="/emerald.png" alt="" width="20px">
            Emerald Devs
            
          </a>
        </p>

      </div>

    </div>
  </footer>
</template>