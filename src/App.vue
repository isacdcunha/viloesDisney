<script setup></script>

<template>
  <header class="fixed top-0 left-0 w-full h-32 bg-white flex items-center px-4">
    <h1 class="nome text-6xl mr-12">Essência sombria</h1>

    <div class="flex items-center px-4">
      <img
        width="30"
        height="30"
        src="https://img.icons8.com/ios-glyphs/60/user--v1.png"
        alt="user--v1"
      />
      <div class="flex flex-col">
        <p class="text-xs ml-2">Olá, visitante!</p>
        <p class="text-xs ml-2">Entrar/Cadastrar</p>
      </div>
    </div>

    <div class="relative mx-10">
    <input
      type="text"
      v-model="query"
      @input="search"
      class="py-2 pl-4 pr-10 border border-black rounded-md focus:outline-none focus:ring-2 focus:ring-blue-500"
      placeholder="Buscar..."
    />
    <svg
      class="absolute right-4 top-1/2 transform -translate-y-1/2 text-gray-500"
      xmlns="http://www.w3.org/2000/svg"
      x="0px"
      y="0px"
      width="20"
      height="20"
      viewBox="0,0,256,256"
    >
      <g fill="#e0e0e0" fill-rule="nonzero" stroke="none" stroke-width="1" stroke-linecap="butt" stroke-linejoin="miter" stroke-miterlimit="10" stroke-dasharray="" stroke-dashoffset="0" font-family="none" font-weight="none" font-size="none" text-anchor="none" style="mix-blend-mode: normal">
        <g transform="scale(5.12,5.12)">
          <path d="M21,3c-9.37891,0 -17,7.62109 -17,17c0,9.37891 7.62109,17 17,17c3.71094,0 7.14063,-1.19531 9.9375,-3.21875l13.15625,13.125l2.8125,-2.8125l-13,-13.03125c2.55469,-2.97656 4.09375,-6.83984 4.09375,-11.0625c0,-9.37891 -7.62109,-17 -17,-17zM21,5c8.29688,0 15,6.70313 15,15c0,8.29688 -6.70312,15 -15,15c-8.29687,0 -15,-6.70312 -15,-15c0,-8.29687 6.70313,-15 15,-15z"></path>
        </g>
      </g>
    </svg>
  </div>
  </header>

  <main class="pt-32">
    <div class="bg-gray-300 w-full py-20">
      <!-- Conteúdo do Main -->
    </div>
  </main>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Italianno&display=swap');

.nome {
  font-family: Italianno, serif;
}
</style>
