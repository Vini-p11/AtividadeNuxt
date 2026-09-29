<template>
  <div data-theme="corporate" class="min-h-screen flex flex-col bg-base-100 text-base-content font-sans antialiased selection:bg-primary selection:text-white">
    <!-- Navbar global com roteamento SPA -->
    <Navbar />

    <!-- Conteúdo dinâmico das rotas gerenciado pelo NuxtPage -->
    <main class="flex-grow">
      <NuxtPage />
    </main>

    <!-- Rodapé -->
    <Footer />
  </div>
</template>

<script setup>
useSeoMeta({
  title: 'Nuxt YouTube - Projeto Prático',
  description: 'Aplicação prática em Nuxt 3 com Vue.js, Tailwind CSS e DaisyUI reproduzindo o projeto da aula com formulário reativo.',
  ogTitle: 'Nuxt YouTube - Projeto Prático',
  ogDescription: 'Aplicação prática em Nuxt 3 com Vue.js, Tailwind CSS e DaisyUI reproduzindo o projeto da aula com formulário reativo.',
  twitterCard: 'summary_large_image'
})
</script>
