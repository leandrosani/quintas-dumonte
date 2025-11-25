🏡 Quintas Dumonte - Landing Page

🔗 Acesse o site: quintasdumonte.com.br

Uma landing page moderna, mobile-first e focada em conversão para o empreendimento Quintas Dumonte, localizado em Domingos Martins - ES.

O projeto foi desenvolvido para apresentar lotes de alto padrão, destacando a natureza, segurança e exclusividade do local, com foco em levar o cliente para o WhatsApp.

🚀 Tecnologias Utilizadas

Nuxt 3: Framework Vue.js para performance e SEO.

Tailwind CSS: Estilização utilitária e responsiva.

Nuxt UI: Biblioteca de componentes e ícones.

GitHub Pages: Hospedagem estática gratuita e rápida.

✨ Funcionalidades

Design Premium: Cores personalizadas (Dourado #D8C67A e Preto #101010).

Responsividade Total: Layout adaptado para Celular, Tablet e Desktop.

Galeria Interativa: Slider de fotos com suporte a touch e proporções inteligentes (Quadrado no mobile, Widescreen no PC).

SEO Otimizado: Metadados configurados, Sitemap, Open Graph (WhatsApp) e dados estruturados (Schema.org) para o Google.

Performance: Carregamento de imagens otimizado (Lazy Loading, Preload, WebP).

Navegação Suave: Scroll suave entre as seções com ajuste de cabeçalho fixo.

🛠️ Como Rodar Localmente

Certifique-se de ter o Node.js instalado.

Clone o repositório:

git clone [https://github.com/seu-usuario/quintas-dumonte.git](https://github.com/seu-usuario/quintas-dumonte.git)



Instale as dependências:

pnpm install



Rode o servidor de desenvolvimento:

pnpm run dev



O site estará disponível em http://localhost:3000.

🌍 Como Fazer o Deploy (Colocar no Ar)

Este projeto está configurado para hospedagem estática no GitHub Pages.

Passo a Passo:

Faça suas alterações no código.

Salve o código na branch principal:

git add .
git commit -m "Descrição da alteração"
git push origin main



Rode o comando de deploy:

pnpm run deploy



Este comando irá gerar os arquivos estáticos e enviá-los automaticamente para a branch gh-pages, atualizando o site em minutos.

📁 Estrutura do Projeto

components/: Blocos de construção do site (Hero, Galeria, Header, etc).

pages/index.vue: A página principal que organiza as seções e contém o SEO.

public/: Arquivos estáticos (Imagens, Favicon, CNAME, Sitemap).

assets/css/: Estilos globais e configurações de fonte.

nuxt.config.ts: Configuração central do Nuxt e Tailwind.

🎨 Personalização

Cores

As cores principais estão definidas no tailwind.config.ts (ou nuxt.config.ts) e no CSS global.

Brand Sand (Dourado): #D8C67A

Brand Black (Preto): #101010

Fontes

O projeto utiliza fontes do Google Fonts, carregadas via CSS:

Títulos: Playfair Display (Serifada).

Texto: Inter (Sans-serif).

Desenvolvido por *Emerald Devs*
