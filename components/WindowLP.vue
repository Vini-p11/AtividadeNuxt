<template>
  <div class="w-full max-w-4xl mx-auto my-6 px-4">
    <div class="mockup-window border border-base-300 bg-base-300 shadow-2xl">
      <div class="flex flex-col items-center justify-center px-6 py-16 bg-base-200 text-center">
        <div class="badge badge-primary badge-outline mb-3 font-medium">Componente DaisyUI WindowLP</div>
        <h2 class="text-3xl md:text-4xl font-black mb-4 text-base-content">
          Exemplo da nossa aplicação
        </h2>
        <p class="max-w-lg text-base text-base-content/80 mb-6">
          Esta tela representa o segundo componente demonstrado no vídeo do Patrick Monteiro (<code class="bg-base-300 px-2 py-1 rounded text-primary">WindowLP.vue</code>), 
          renderizado na rota automática <code class="bg-base-300 px-2 py-1 rounded text-primary">/example</code> pelo sistema de roteamento do Nuxt.
        </p>

        <!-- Detalhes do sistema de páginas e rotas -->
        <div class="stats stats-vertical lg:stats-horizontal shadow bg-base-100 mb-8 border border-base-300">
          <div class="stat place-items-center">
            <div class="stat-title">Rota Atual</div>
            <div class="stat-value text-primary text-2xl">/example</div>
            <div class="stat-desc">Mapeada de pages/example.vue</div>
          </div>
          <div class="stat place-items-center">
            <div class="stat-title">Renderização</div>
            <div class="stat-value text-secondary text-2xl">SSR</div>
            <div class="stat-desc">Server-Side Rendered</div>
          </div>
          <div class="stat place-items-center">
            <div class="stat-title">Automação</div>
            <div class="stat-value text-accent text-2xl">100%</div>
            <div class="stat-desc">Auto-import de Componentes</div>
          </div>
        </div>

        <div class="flex flex-wrap gap-4 justify-center">
          <NuxtLink to="/" class="btn btn-outline">
            <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 mr-1" fill="none" viewBox="0 0 24 24" stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M10 19l-7-7m0 0l7-7m-7 7h18" />
            </svg>
            Voltar para o Início
          </NuxtLink>
          <NuxtLink to="/cadastro" class="btn btn-primary">
            Ir para o Formulário de Cadastro
            <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 ml-1" fill="none" viewBox="0 0 24 24" stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M14 5l7 7m0 0l-7 7m7-7H3" />
            </svg>
          </NuxtLink>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
// WindowLP componente reproduzido fielmente da aula de Nuxt
</script>
