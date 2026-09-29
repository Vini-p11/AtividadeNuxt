# 🚀 Projeto Prático: Nuxt.js + Vue 3 + Tailwind CSS + DaisyUI

Aplicação web moderna desenvolvida para consolidar os conceitos da stack **Node.js**, **Vue.js (Vue 3 com Composition API)** e **Nuxt 3 (SSR)**.

O projeto reproduz a aplicação construída na aula prática do canal *Vuejs Expert* (Patrick Monteiro) — demonstrando SSR, Tailwind CSS, DaisyUI e roteamento nativo — e implementa uma nova funcionalidade completa: uma **página de formulário de cadastro de membros (`/cadastro`)** com validação reativa, feedback visual e registro estruturado no console.

---

## 📋 Sumário
1. [Stack Tecnológica](#-stack-tecnológica)
2. [Estrutura do Projeto](#-estrutura-do-projeto)
3. [Como Executar o Projeto Localmente](#-como-executar-o-projeto-localmente)
4. [Funcionalidades Implementadas](#-funcionalidades-implementadas)
   - [Parte A: Reprodução do Projeto Base](#parte-a-reprodução-do-projeto-base)
   - [Parte B: Nova Página com Formulário de Cadastro](#parte-b-nova-página-com-formulário-de-cadastro)
5. [Roteiro para Gravação do Vídeo de Demonstração (2 a 3 min)](#-roteiro-para-gravação-do-vídeo-de-demonstração-2-a-3-min)
6. [Critérios de Avaliação Atendidos](#-critérios-de-avaliação-atendidos)

---

## 🛠 Stack Tecnológica

- **Node.js** (v20+ / v22 LTS)
- **Nuxt 3** (Framework Vue fullstack com SSR e roteamento baseado em arquivos)
- **Vue.js 3** (Composition API: `reactive`, `ref`, `computed`, `v-model`)
- **Tailwind CSS** (Estilização utilitária e responsiva)
- **DaisyUI** (Componentes semânticos e temas modernos)
- **Vite & Nitro Engine** (Build ultra-rápido e servidor de renderização moderna)

---

## 📁 Estrutura do Projeto

```text
├── assets/
│   └── css/
│       └── tailwind.css         # Importações do Tailwind CSS (@tailwind base, components, utilities)
├── components/
│   ├── Navbar.vue               # Barra de navegação com links SPA (Início, Exemplo, Cadastro)
│   ├── HeroLP.vue               # Componente Hero da aula prática com botão de navegação
│   ├── WindowLP.vue             # Componente Mockup Window da aula prática
│   └── Footer.vue               # Rodapé com informações da aplicação
├── pages/
│   ├── index.vue                # Rota '/' com o componente HeroLP
│   ├── example.vue              # Rota '/example' com o componente WindowLP
│   └── cadastro.vue             # Rota '/cadastro' (Parte B) - Formulário completo e reativo
├── app.vue                      # Componente raiz com Navbar, NuxtPage (<NuxtPage />) e Footer
├── nuxt.config.ts               # Configurações do Nuxt (SSR: true, módulos, metatags SEO)
├── tailwind.config.ts           # Configuração do Tailwind CSS e plugin do DaisyUI
├── package.json                 # Dependências e scripts npm
└── README.md                    # Documentação do projeto e instruções de execução
```

---

## 💻 Como Executar o Projeto Localmente

### Pré-requisitos
- Node.js instalado (versão 18+ recomendada)
- Gerenciador de pacotes `npm`

### 1. Clonar ou Acessar o Repositório
```bash
git clone <URL_DO_REPOSITORIO>
cd <NOME_DA_PASTA>
```

### 2. Instalar as Dependências
```bash
npm install
```

### 3. Iniciar o Servidor de Desenvolvimento
```bash
npm run dev
```
A aplicação estará disponível em: **`http://localhost:3000`**

### 4. Compilar para Produção (Opcional / Teste de Build)
```bash
npm run build
npm run preview
```

---

## ⚙ Funcionalidades Implementadas

### Parte A: Reprodução do Projeto Base
- **Renderização SSR:** Habilitada via `ssr: true` no `nuxt.config.ts`.
- **Roteamento Automático Nuxt:** As pastas dentro de `pages/` definem as rotas sem necessidade de configuração manual do Vue Router.
- **Componentes do Vídeo:**
  - `HeroLP.vue`: Contém o componente Hero do DaisyUI com botão de navegação chamando `useRouter().push('/example')`.
  - `WindowLP.vue`: Contém o componente Mockup Window exibindo *"Exemplo da nossa aplicação"*.
  - `useSeoMeta()`: Configuração de títulos e metatags para indexação e performance.

### Parte B: Nova Página com Formulário de Cadastro (`/cadastro`)
Formulário interativo com validação em tempo real e reatividade total via Composition API:
1. **Nome Completo:** Input de texto com validação obrigatória (mínimo de 3 caracteres).
2. **E-mail:** Input de e-mail com validação obrigatória e checagem de formato válido via expressão regular.
3. **Curso / Área de Atuação:** Dropdown (`<select>`) com opções acadêmicas e de tecnologia.
4. **Semestre / Período:** Dropdown (`<select>`) com opções de 1º a 10º semestre.
5. **Interesses / Habilidades:** Grade de checkboxes reativos (Front-end, Back-end, Mobile, UI/UX, DevOps, IA, Banco de Dados, Segurança), exigindo a seleção de pelo menos uma área.
6. **Mensagem / Bio Curta:** Textarea com limite de 250 caracteres e contador reativo dinâmico que muda de cor conforme se aproxima do limite.
7. **Feedback Visual:**
   - Alerta de sucesso (`alert alert-success`) com card de resumo detalhado do membro cadastrado.
   - Log estilizado e formatado no Console do navegador (`console.table`).
   - Botão para limpar campos e reiniciar o formulário reativamente.
   - Mensagens de erro visuais sob cada campo inválido (`input-error`, `select-error`).

---

## 🎥 Roteiro para Gravação do Vídeo de Demonstração (2 a 3 min)

Para a gravação exigida na entrega (via Loom, OBS Studio ou captura do Windows com `Win + G` / Ferramenta de Captura):

1. **Abertura (0:00 - 0:30):**
   - Abra o navegador em `http://localhost:3000`.
   - Mostre a tela inicial com o Hero (`HeroLP.vue`), o badge da stack e a barra de navegação superior.
   - Clique no botão **"Go to Example"** ou no link do menu para navegar até `/example`.

2. **Navegação SPA e Demonstração do Vídeo Base (0:30 - 1:00):**
   - Na página `/example`, mostre o componente de janela (`WindowLP.vue`) com o título *"Exemplo da nossa aplicação"*.
   - Destaque que a navegação ocorreu de forma instantânea (SPA) pelo sistema de rotas do Nuxt.

3. **Demonstração do Formulário e Validações (1:00 - 2:00):**
   - Clique em **"Novo Membro (Cadastro)"** na navbar ou no botão da página para ir até `/cadastro`.
   - Abra as Ferramentas do Desenvolvedor no navegador (**F12** ou `Ctrl + Shift + I`) na aba **Console**.
   - **Teste de Validação:** Clique diretamente no botão **"Enviar Cadastro"** sem preencher nada.
     - Mostre que os campos obrigatórios ficam destacados em vermelho com mensagens de erro (Nome, E-mail, Curso, Semestre, Interesses).
   - Digite um e-mail inválido (ex: `teste@invalido`) e mostre o aviso de formato incorreto.

4. **Preenchimento e Envio com Sucesso (2:00 - 2:45):**
   - Preencha todos os campos com dados válidos:
     - Nome: *Seu Nome Completo*
     - E-mail: *seu.email@exemplo.com*
     - Curso: Selecione *Engenharia de Software* (ou outro)
     - Semestre: Selecione *5º Semestre*
     - Interesses: Marque 2 ou mais opções (ex: *Front-end*, *UI/UX Design*)
     - Bio: Digite uma mensagem breve e aponte para o contador de caracteres reativo `X / 250`.
   - Clique no botão **"Enviar Cadastro"**.
   - Mostre o feedback:
     - O alerta verde de sucesso na tela.
     - O card com o resumo dos dados cadastrados.
     - O log estilizado e a tabela no **Console do Navegador** (`console.table`).
   - Mostre o botão "Novo Cadastro" ou "Limpar Campos" resetando o formulário reativamente.

---

## 📊 Critérios de Avaliação Atendidos

| Critério | Status | Detalhes |
|---|:---:|---|
| **Fidelidade ao Projeto Base** | ✅ Concluído | Nuxt 3 com SSR ativo, Tailwind CSS, DaisyUI, `HeroLP.vue` e `WindowLP.vue`. |
| **Estrutura Nuxt/Vue** | ✅ Concluído | Diretório `pages/` com `index.vue`, `example.vue` e `cadastro.vue`, `components/`, e Composition API (`ref`, `reactive`, `computed`). |
| **Qualidade do Formulário** | ✅ Concluído | Todos os campos solicitados (Nome, Email, Curso, Semestre, Interesses, Bio com contador), validação robusta e feedback visual completo. |
| **Roteamento SPA** | ✅ Concluído | Navbar integrada com `NuxtLink` permitindo alternar suavemente entre todas as rotas. |
| **Documentação (README)** | ✅ Concluído | Instruções claras de instalação, execução e roteiro do vídeo de demonstração. |
