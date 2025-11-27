<script setup lang="ts">
/**
 * Componente: SectionLocation (Localização)
 * Função: Mostrar o mapa e reforçar a acessibilidade do local.
 */

// Endereço para exibir e usar nos links
const address = {
  street: 'Rua Tijuco Preto',
  district: 'Domingos Martins',
  city: 'Domingos Martins - ES',
  full: 'Rua Tijuco Preto, Paraju, Domingos Martins - ES'
}

// Links para abrir aplicativos de navegação direto
// (Substitua pelas coordenadas exatas depois para maior precisão se tiver)
const mapsLink = `https://www.google.com/maps/search/?api=1&query=${encodeURIComponent(address.full)}`
</script>

<template>
  <section class="bg-white py-16 sm:py-32" id="location">
    <div class="mx-auto max-w-7xl px-6 lg:px-8">
      
      <div class="grid grid-cols-1 lg:grid-cols-2 gap-16 items-center">
        
        <div class="-mt-16 lg:mt-0 order-2 lg:order-1">
          <p class="mt-6 text-lg leading-relaxed text-gray-600">
            Localizado em uma das regiões mais valorizadas de Domingos Martins. 
          </p>

          <ul role="list" class="mt-8 space-y-4 text-gray-600">
            <li class="flex gap-x-3">
              <UIcon name="material-symbols-light:check-rounded" class="mt-1 h-5 w-5 flex-none text-[#81785d]" aria-hidden="true" />
              <span><strong class="font-semibold text-[#101010]">Região Segura:</strong> Vizinhança tranquila e familiar.</span>
            </li>
            <li class="flex gap-x-3">
              <UIcon name="material-symbols-light:check-rounded" class="mt-1 h-5 w-5 flex-none text-[#81785d]" aria-hidden="true" />
              <span><strong class="font-semibold text-[#101010]">Clima Diversificado:</strong> Aproximadamente 5°C no inverno e 30ºC no verão, aproveitando os dois extremos, lareira e piscina.</span>
            </li>
            <li class="flex gap-x-3">
              <UIcon name="material-symbols-light:check-rounded" class="mt-1 h-5 w-5 flex-none text-[#81785d]" aria-hidden="true" />
              <span><strong class="font-semibold text-[#101010]">Privacidade:</strong> O Quintas Dumonte fica em final da estrada, garantindo privacidade sem circulação de veículos ou pessoas que não sejam moradores.</span>
            </li>
            <li class="flex gap-x-3">
              <UIcon name="material-symbols-light:check-rounded" class="mt-1 h-5 w-5 flex-none text-[#81785d]" aria-hidden="true" />
              <span><strong class="font-semibold text-[#101010]">Contato Direto com a Natureza
              :</strong> Aqui, o verde está por todos os lados, pássaros divérsos e animais silvéstres, área de preservação ambiental para caminhar, descansar ou só apreciar o momento.
              </span>
            </li>
            <li class="flex gap-x-3">
              <UIcon name="material-symbols-light:check-rounded" class="mt-1 h-5 w-5 flex-none text-[#81785d]" aria-hidden="true" />
              <span><strong class="font-semibold text-[#101010]">Infraestrutura Completa
              :</strong> Água, luz, internet, lagoas, trilhas e estradas.</span>
            </li>
            <li class="flex gap-x-3">
              <UIcon name="material-symbols-light:check-rounded" class="mt-1 h-5 w-5 flex-none text-[#81785d]" aria-hidden="true" />
              <span><strong class="font-semibold text-[#101010]">Recursos próximos
              :</strong> Vila a 1km com supermercado, farmácia, lanchonetes, postos de saúde e combustível, academia, lojas, igreja...</span>
            </li>
          </ul>
        </div>

        <div>
          <h2 class="mb-6 text-base font-semibold leading-7 text-[#7c5f42] uppercase tracking-wide">
            Localização Privilegiada
          </h2>
          <h3 class="mb-6 text-2xl font-bold tracking-tight text-[#101010] sm:text-4xl">
            O clima das montanhas, <br />
            no interior de Domingos Martins.
          </h3>
            <div class="order-1 lg:order-2 h-full relative rounded-2xl overflow-hidden shadow-xl bg-gray-50">
            <img src="/quintas-social.jpg" alt="" loading="lazy" class="w-full h-full object-cover">
          </div>
        </div>
        


      </div>
    </div>
  </section>
</template>