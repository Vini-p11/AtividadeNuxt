<template>
  <div class="hero min-h-[calc(100vh-8rem)] bg-base-200 py-12">
    <div class="hero-content text-center">
      <div class="max-w-2xl px-4">
        <div class="badge badge-accent badge-outline mb-4 font-semibold px-4 py-3">
          Nuxt 3 + SSR + Tailwind CSS + DaisyUI
        </div>
        <h1 class="text-4xl md:text-6xl font-extrabold tracking-tight text-base-content leading-tight">
          Hello there! 👋
        </h1>
        <p class="py-6 text-lg md:text-xl text-base-content/80 max-w-xl mx-auto leading-relaxed">
          Esta é a aplicação prática reproduzida a partir da aula de Nuxt com Vue 3. 
          Aqui demonstramos o roteamento baseado em arquivos, componentes reutilizáveis, 
          renderização SSR e a integração completa com DaisyUI.
        </p>
        <div class="flex flex-col sm:flex-row gap-4 justify-center items-center mt-2">
          <button class="btn btn-primary btn-lg shadow-lg w-full sm:w-auto" @click="goToExample">
            Go to Example
            <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 ml-1" fill="none" viewBox="0 0 24 24" stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M14 5l7 7m0 0l-7 7m7-7H3" />
            </svg>
          </button>
          <NuxtLink to="/cadastro" class="btn btn-outline btn-lg w-full sm:w-auto">
            Ir para Cadastro
          </NuxtLink>
        </div>

        <!-- Cards de Destaques Técnicos -->
        <div class="grid grid-cols-1 sm:grid-cols-3 gap-4 mt-12 text-left">
          <div class="card bg-base-100 shadow-md border border-base-200 p-4">
            <div class="font-bold text-primary text-base">⚡ Nuxt 3 SSR</div>
            <div class="text-xs text-base-content/70 mt-1">Renderização do lado do servidor habilitada para máximo desempenho e SEO.</div>
          </div>
          <div class="card bg-base-100 shadow-md border border-base-200 p-4">
            <div class="font-bold text-accent text-base">🎨 DaisyUI + Tailwind</div>
            <div class="text-xs text-base-content/70 mt-1">Componentes estilizados e responsivos prontos para produção.</div>
          </div>
          <div class="card bg-base-100 shadow-md border border-base-200 p-4">
            <div class="font-bold text-secondary text-base">📝 Novo Formulário</div>
            <div class="text-xs text-base-content/70 mt-1">Página reativa com v-model, validação completa e feedback visual.</div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
const router = useRouter()

function goToExample() {
  router.push('/example')
}
</script>
