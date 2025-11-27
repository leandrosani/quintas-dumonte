<script setup lang="ts">
/**
 * Página: Home (Index)
 * Função: Orquestrar a exibição de todas as seções da Landing Page.
 */

// URL Final do Site (Com www, conforme seu snippet)
const siteUrl = 'https://www.quintasdumonte.com.br' 

// 1. SEO e Metadados
useSeoMeta({
  title: 'Terrenos e chácaras em sítio de lazer em Domingos Martins | Quintas Dumonte – Montanhas Capixabas',
  description: 'Terrenos e chácaras em sítio de lazer em Domingos Martins – Montanhas Capixabas, descanso e contato com a natureza nas Montanhas Capixabas. Agende sua visita.',
  ogTitle: 'Terrenos e chácaras em sítio de lazer em Domingos Martins | Quintas Dumonte – Montanhas Capixabas',
  ogDescription: 'Terrenos e chácaras em sítio de lazer em Domingos Martins – Montanhas Capixabas, descanso e contato com a natureza nas Montanhas Capixabas. Agende sua visita.',
  ogImage: `${siteUrl}/quintas-social.jpg`,
  ogUrl: siteUrl,
  ogType: 'website',
  ogLocale: 'pt_BR',
  twitterCard: 'summary_large_image',
  twitterTitle: 'Terrenos e chácaras em sítio de lazer em Domingos Martins | Quintas Dumonte – Montanhas Capixabas',
  twitterDescription: 'Terrenos e chácaras em sítio de lazer em Domingos Martins | Quintas Dumonte – Montanhas Capixabas.',
  twitterImage: `${siteUrl}/quintas-social.jpg`,
})

// 2. Dados Estruturados e Otimizações
useHead({
  meta: [
    { name: 'google-site-verification', content: 'Mld7rqhhKlkWPw75sjlUth6kVveFqxTIpb3ZF6tk8zQ' }
  ],
  link: [
    { rel: 'canonical', href: siteUrl },
    { rel: 'icon', type: 'image/png', href: '/favicon.png' },
    // Preload da imagem Hero para carregamento instantâneo (Melhora LCP)
    { 
      rel: 'preload', 
      as: 'image', 
      href: '/foto-hero.webp', 
      fetchpriority: 'high'
    }
  ],
  htmlAttrs: {
    lang: 'pt-BR'
  },
  script: [
    {
      type: 'application/ld+json',
      innerHTML: JSON.stringify({
        "@context": "https://schema.org",
        "@type": "LandPlot",
        "name": "Terrenos e chácaras em sítio de lazer Quintas Dumonte",
        "description": "Terrenos e chácaras em sítio de lazer em Domingos Martins, região das Montanhas Capixabas.",
        "address": {
          "@type": "PostalAddress",
          "addressLocality": "Domingos Martins",
          "addressRegion": "ES",
          "addressCountry": "BR"
        },
        "geo": {
          "@type": "GeoCoordinates",
          "latitude": -20.363,
          "longitude": -40.659
        },
        "url": siteUrl,
        "image": [`${siteUrl}/foto-hero.webp`],
        "offers": {
          "@type": "Offer",
          "price": "Sob consulta",
          "priceCurrency": "BRL",
          "availability": "https://schema.org/InStock"
        }
      })
    }
  ]
})
</script>

<template>
  <div class="bg-white flex flex-col w-full">
    
    <!-- 
      Seção Hero:
      Não precisa de margem pois é o topo absoluto da página.
    -->
    <SectionHero id="intro" />

    <!-- 
      AQUI ESTÁ O SEGREDO DO SCROLL:
      Adicionei a classe 'scroll-mt-24' em todas as seções abaixo.
      
      O que ela faz: Cria uma margem invisível de ~100px no topo da seção
      APENAS quando o navegador rola até ela via âncora (#id).
      Isso impede que o Header fixo fique por cima do título.
    -->

    <SectionLots id="lots" class="scroll-mt-16" />

    <SectionLocation id="location" class="scroll-mt-16" />

    <SectionGallery id="gallery" class="scroll-mt-16" />

    <SectionFeatures id="features" class="scroll-mt-16" />

    <SectionContact id="contact" class="scroll-mt-16" />

    

  </div>
</template>