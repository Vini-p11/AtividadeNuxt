<template>
  <header class="navbar bg-base-100 border-b border-base-200 px-4 md:px-8 sticky top-0 z-50 shadow-sm">
    <div class="navbar-start">
      <div class="dropdown">
        <label tabindex="0" class="btn btn-ghost lg:hidden" aria-label="Abrir menu">
          <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h8m-8 6h16" />
          </svg>
        </label>
        <ul tabindex="0" class="menu menu-sm dropdown-content mt-3 z-[1] p-2 shadow bg-base-100 rounded-box w-52">
          <li><NuxtLink to="/" active-class="active">Início</NuxtLink></li>
          <li><NuxtLink to="/example" active-class="active">Exemplo</NuxtLink></li>
          <li><NuxtLink to="/cadastro" active-class="active">Novo Membro</NuxtLink></li>
        </ul>
      </div>
      <NuxtLink to="/" class="btn btn-ghost normal-case text-xl font-bold flex items-center gap-2">
        <span class="text-emerald-500 text-2xl font-black">▲</span>
        <span>Nuxt <span class="text-primary">YouTube</span></span>
      </NuxtLink>
    </div>

    <div class="navbar-center hidden lg:flex">
      <ul class="menu menu-horizontal px-1 font-medium gap-1">
        <li>
          <NuxtLink to="/" active-class="active font-semibold text-primary" class="rounded-lg">
            Início
          </NuxtLink>
        </li>
        <li>
          <NuxtLink to="/example" active-class="active font-semibold text-primary" class="rounded-lg">
            Exemplo
          </NuxtLink>
        </li>
        <li>
          <NuxtLink to="/cadastro" active-class="active font-semibold text-primary" class="rounded-lg">
            Novo Membro (Cadastro)
          </NuxtLink>
        </li>
      </ul>
    </div>

    <div class="navbar-end gap-2">
      <NuxtLink to="/cadastro" class="btn btn-primary btn-sm md:btn-md shadow-md">
        Cadastrar
      </NuxtLink>
    </div>
  </header>
</template>
