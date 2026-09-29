<template>
  <div class="py-10 px-4 max-w-4xl mx-auto">
    <!-- Cabeçalho da Página -->
    <div class="text-center mb-8">
      <div class="badge badge-primary badge-outline mb-2 font-medium">Parte B - Nova Funcionalidade</div>
      <h1 class="text-3xl md:text-5xl font-extrabold text-base-content tracking-tight">
        Formulário de Cadastro
      </h1>
      <p class="text-base text-base-content/70 mt-2 max-w-xl mx-auto">
        Cadastre um novo membro na comunidade. Demonstração do uso da Composition API do Vue 3 (<code class="bg-base-200 px-1 py-0.5 rounded text-primary">reactive</code>, <code class="bg-base-200 px-1 py-0.5 rounded text-primary">ref</code>, <code class="bg-base-200 px-1 py-0.5 rounded text-primary">v-model</code>) e validação reativa.
      </p>
    </div>

    <!-- Alerta de Sucesso -->
    <div v-if="submittedSuccess" class="alert alert-success shadow-lg mb-8 transition-all duration-300">
      <svg xmlns="http://www.w3.org/2000/svg" class="stroke-current shrink-0 h-6 w-6" fill="none" viewBox="0 0 24 24">
        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z" />
      </svg>
      <div class="flex-1">
        <h3 class="font-bold text-lg">Cadastro Realizado com Sucesso!</h3>
        <div class="text-sm">Os dados foram validados e registrados no estado reativo da aplicação e no console do navegador.</div>
      </div>
      <button class="btn btn-sm btn-outline" @click="resetForm">Novo Cadastro</button>
    </div>

    <!-- Card de Confirmação com Dados Submetidos -->
    <div v-if="submittedSuccess && lastSubmittedData" class="card bg-base-100 shadow-xl border border-success/30 mb-8 p-6">
      <div class="flex items-center justify-between border-b pb-4 mb-4">
        <h3 class="text-xl font-bold text-success flex items-center gap-2">
          <span>✓</span> Membro Cadastrado
        </h3>
        <span class="badge badge-success text-white font-medium">Ativo</span>
      </div>
      <div class="grid grid-cols-1 md:grid-cols-2 gap-4 text-sm">
        <div><span class="font-semibold text-base-content/70">Nome:</span> <span class="font-medium text-base-content">{{ lastSubmittedData.nome }}</span></div>
        <div><span class="font-semibold text-base-content/70">E-mail:</span> <span class="font-medium text-base-content">{{ lastSubmittedData.email }}</span></div>
        <div><span class="font-semibold text-base-content/70">Curso / Área:</span> <span class="font-medium text-base-content">{{ lastSubmittedData.curso }}</span></div>
        <div><span class="font-semibold text-base-content/70">Semestre / Período:</span> <span class="font-medium text-base-content">{{ lastSubmittedData.semestre }}º Semestre</span></div>
        <div class="md:col-span-2">
          <span class="font-semibold text-base-content/70">Interesses:</span>
          <div class="flex flex-wrap gap-1 mt-1">
            <span v-for="skill in lastSubmittedData.interesses" :key="skill" class="badge badge-primary badge-sm">
              {{ skill }}
            </span>
          </div>
        </div>
        <div v-if="lastSubmittedData.bio" class="md:col-span-2">
          <span class="font-semibold text-base-content/70">Bio / Mensagem:</span>
          <p class="italic bg-base-200 p-3 rounded-lg mt-1 text-base-content/90">{{ lastSubmittedData.bio }}</p>
        </div>
      </div>
    </div>

    <!-- Card Principal do Formulário -->
    <div class="card bg-base-100 shadow-2xl border border-base-200">
      <form @submit.prevent="handleSubmit" class="card-body p-6 md:p-10 space-y-6">
        
        <!-- Campo: Nome Completo -->
        <div class="form-control w-full">
          <label class="label">
            <span class="label-text font-semibold text-base">Nome Completo <span class="text-error">*</span></span>
          </label>
          <input 
            v-model.trim="form.nome" 
            type="text" 
            placeholder="Ex: Ana Silva Oliveira" 
            class="input input-bordered w-full transition-colors"
            :class="{ 'input-error': errors.nome }"
            @input="validateField('nome')"
          />
          <label v-if="errors.nome" class="label">
            <span class="label-text-alt text-error font-medium">{{ errors.nome }}</span>
          </label>
        </div>

        <!-- Campo: E-mail -->
        <div class="form-control w-full">
          <label class="label">
            <span class="label-text font-semibold text-base">E-mail <span class="text-error">*</span></span>
          </label>
          <input 
            v-model.trim="form.email" 
            type="email" 
            placeholder="Ex: ana.silva@exemplo.com" 
            class="input input-bordered w-full transition-colors"
            :class="{ 'input-error': errors.email }"
            @input="validateField('email')"
          />
          <label v-if="errors.email" class="label">
            <span class="label-text-alt text-error font-medium">{{ errors.email }}</span>
          </label>
        </div>

        <!-- Linha Dupla: Curso e Semestre -->
        <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
          <!-- Campo: Curso / Área de Atuação -->
          <div class="form-control w-full">
            <label class="label">
              <span class="label-text font-semibold text-base">Curso / Área de Atuação <span class="text-error">*</span></span>
            </label>
            <select 
              v-model="form.curso" 
              class="select select-bordered w-full transition-colors"
              :class="{ 'select-error': errors.curso }"
              @change="validateField('curso')"
            >
              <option disabled value="">Selecione seu curso ou área...</option>
              <option value="Engenharia de Software">Engenharia de Software</option>
              <option value="Ciência da Computação">Ciência da Computação</option>
              <option value="Sistemas de Informação">Sistemas de Informação</option>
              <option value="Análise e Desenvolvimento de Sistemas">Análise e Desenvolvimento de Sistemas</option>
              <option value="Engenharia da Computação">Engenharia da Computação</option>
              <option value="Design Digital / UI-UX">Design Digital / UI-UX</option>
              <option value="Outro">Outro</option>
            </select>
            <label v-if="errors.curso" class="label">
              <span class="label-text-alt text-error font-medium">{{ errors.curso }}</span>
            </label>
          </div>

          <!-- Campo: Semestre / Período -->
          <div class="form-control w-full">
            <label class="label">
              <span class="label-text font-semibold text-base">Semestre / Período <span class="text-error">*</span></span>
            </label>
            <select 
              v-model.number="form.semestre" 
              class="select select-bordered w-full transition-colors"
              :class="{ 'select-error': errors.semestre }"
              @change="validateField('semestre')"
            >
              <option disabled value="">Selecione o semestre atual...</option>
              <option v-for="n in 10" :key="n" :value="n">{{ n }}º Semestre</option>
            </select>
            <label v-if="errors.semestre" class="label">
              <span class="label-text-alt text-error font-medium">{{ errors.semestre }}</span>
            </label>
          </div>
        </div>

        <!-- Campo: Interesses / Habilidades (Checkboxes) -->
        <div class="form-control w-full">
          <label class="label pb-1">
            <span class="label-text font-semibold text-base">Interesses / Habilidades <span class="text-error">*</span></span>
            <span class="label-text-alt text-base-content/60">Selecione pelo menos um</span>
          </label>
          <div class="grid grid-cols-2 sm:grid-cols-3 md:grid-cols-4 gap-3 mt-2 bg-base-200/50 p-4 rounded-xl border border-base-200">
            <label 
              v-for="item in listaInteresses" 
              :key="item" 
              class="cursor-pointer label justify-start gap-3 bg-base-100 p-2.5 rounded-lg border border-base-300 hover:border-primary transition-colors shadow-xs"
            >
              <input 
                type="checkbox" 
                :value="item" 
                v-model="form.interesses" 
                class="checkbox checkbox-primary checkbox-sm"
                @change="validateField('interesses')"
              />
              <span class="label-text text-sm font-medium">{{ item }}</span>
            </label>
          </div>
          <label v-if="errors.interesses" class="label">
            <span class="label-text-alt text-error font-medium">{{ errors.interesses }}</span>
          </label>
        </div>

        <!-- Campo: Mensagem / Bio Curta com contador -->
        <div class="form-control w-full">
          <div class="label">
            <span class="label-text font-semibold text-base">Mensagem / Bio Curta</span>
            <span class="label-text-alt font-mono" :class="charsRemainingClass">
              {{ form.bio.length }} / {{ maxChars }} caracteres
            </span>
          </div>
          <textarea 
            v-model="form.bio" 
            :maxlength="maxChars" 
            rows="3" 
            placeholder="Conte um pouco sobre suas motivações, projetos anteriores ou expectativas..."
            class="textarea textarea-bordered w-full leading-relaxed"
          ></textarea>
        </div>

        <!-- Ações do Formulário -->
        <div class="card-actions justify-end items-center gap-4 pt-4 border-t border-base-200">
          <button 
            type="button" 
            class="btn btn-ghost" 
            @click="resetForm"
          >
            Limpar Campos
          </button>
          <button 
            type="submit" 
            class="btn btn-primary px-8 shadow-md"
            :class="{ 'loading': isSubmitting }"
          >
            <span v-if="!isSubmitting">Enviar Cadastro</span>
            <span v-else>Enviando...</span>
          </button>
        </div>

      </form>
    </div>
  </div>
</template>

<script setup>
import { reactive, ref, computed } from 'vue'

useSeoMeta({
  title: 'Formulário de Cadastro | Nuxt YouTube',
  description: 'Página de formulário de cadastro de novos membros com validação reativa e Composition API.'
})

// Lista pré-definida de habilidades e interesses
const listaInteresses = [
  'Front-end (Vue/Nuxt)',
  'Back-end (Node.js)',
  'Mobile (Flutter/React Native)',
  'UI/UX Design',
  'DevOps & Cloud',
  'Banco de Dados',
  'Inteligência Artificial',
  'Segurança da Informação'
]

const maxChars = 250

// Estado reativo do formulário
const form = reactive({
  nome: '',
  email: '',
  curso: '',
  semestre: '',
  interesses: [],
  bio: ''
})

// Estado de erros de validação
const errors = reactive({
  nome: '',
  email: '',
  curso: '',
  semestre: '',
  interesses: ''
})

const isSubmitting = ref(false)
const submittedSuccess = ref(false)
const lastSubmittedData = ref(null)

// Computed para estilizar o contador de caracteres
const charsRemainingClass = computed(() => {
  const remaining = maxChars - form.bio.length
  if (remaining < 20) return 'text-error font-bold'
  if (remaining < 50) return 'text-warning'
  return 'text-base-content/60'
})

// Função para validar campo individual
function validateField(fieldName) {
  switch (fieldName) {
    case 'nome':
      if (!form.nome) {
        errors.nome = 'O nome completo é obrigatório.'
      } else if (form.nome.trim().length < 3) {
        errors.nome = 'O nome deve ter pelo menos 3 caracteres.'
      } else {
        errors.nome = ''
      }
      break

    case 'email':
      const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/
      if (!form.email) {
        errors.email = 'O e-mail é obrigatório.'
      } else if (!emailRegex.test(form.email)) {
        errors.email = 'Insira um formato de e-mail válido (ex: nome@dominio.com).'
      } else {
        errors.email = ''
      }
      break

    case 'curso':
      if (!form.curso) {
        errors.curso = 'Selecione o seu curso ou área de atuação.'
      } else {
        errors.curso = ''
      }
      break

    case 'semestre':
      if (!form.semestre) {
        errors.semestre = 'Selecione o semestre ou período atual.'
      } else {
        errors.semestre = ''
      }
      break

    case 'interesses':
      if (form.interesses.length === 0) {
        errors.interesses = 'Selecione pelo menos um interesse ou habilidade.'
      } else {
        errors.interesses = ''
      }
      break
  }
}

// Validação completa de todos os campos
function validateAll() {
  validateField('nome')
  validateField('email')
  validateField('curso')
  validateField('semestre')
  validateField('interesses')

  return !errors.nome && !errors.email && !errors.curso && !errors.semestre && !errors.interesses
}

// Submissão do formulário
function handleSubmit() {
  if (!validateAll()) {
    submittedSuccess.value = false
    return
  }

  isSubmitting.value = true

  // Simulação de delay para feedback visual de envio
  setTimeout(() => {
    isSubmitting.value = false
    submittedSuccess.value = true

    // Salva uma cópia profunda dos dados submetidos para o card de feedback
    lastSubmittedData.value = JSON.parse(JSON.stringify(form))

    // Log formatado no console para atender aos requisitos de avaliação
    console.log(
      '%c🎉 NOVO MEMBRO CADASTRADO COM SUCESSO! 🎉',
      'background: #10B981; color: white; font-weight: bold; font-size: 14px; padding: 4px 8px; border-radius: 4px;'
    )
    console.table({
      'Nome Completo': form.nome,
      'E-mail': form.email,
      'Curso / Área': form.curso,
      'Semestre': `${form.semestre}º Semestre`,
      'Interesses': form.interesses.join(', '),
      'Bio Curta': form.bio || '(Sem mensagem)'
    })

    // Rolagem suave até o topo para visualizar o feedback
    if (typeof window !== 'undefined') {
      window.scrollTo({ top: 0, behavior: 'smooth' })
    }
  }, 400)
}

// Limpeza reativa dos campos
function resetForm() {
  form.nome = ''
  form.email = ''
  form.curso = ''
  form.semestre = ''
  form.interesses = []
  form.bio = ''

  errors.nome = ''
  errors.email = ''
  errors.curso = ''
  errors.semestre = ''
  errors.interesses = ''

  submittedSuccess.value = false
  lastSubmittedData.value = null
}
</script>
