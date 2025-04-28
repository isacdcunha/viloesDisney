<script setup></script>

<template>
  <header class="fixed top-0 left-0 w-full h-32 bg-white flex items-center px-4">
    <h1 class="nome text-6xl mr-12 ml-5">Essência sombria</h1>

    <div class="flex items-center px-4">
      <img
        width="25"
        height="25"
        src="https://img.icons8.com/ios-glyphs/60/user--v1.png"
        alt="user--v1"
      />
      <div class="flex flex-col ml-2">
        <p class="text-xs">Olá, visitante!</p>
        <p class="text-xs">Entrar/Cadastrar</p>
      </div>
    </div>

    <div class="flex items-center relative mx-10">
      <div class="relative flex items-center">
        <input
          type="text"
          v-model="query"
          @input="search"
          class="py-2 pl-4 pr-22 border border-black rounded-md focus:outline-none focus:ring-2 focus:ring-blue-500"
          placeholder="Buscar..."
        />
        <svg
          class="absolute right-4 top-1/2 transform -translate-y-1/2 text-gray-500"
          xmlns="http://www.w3.org/2000/svg"
          width="10"
          height="10"
          viewBox="0 0 256 256"
        >
          <g fill="#e0e0e0">
            <g transform="scale(5.12,5.12)">
              <path
                d="M21,3c-9.37891,0-17,7.62109-17,17c0,9.37891,7.62109,17,17,17c3.71094,0,7.14063-1.19531,9.9375-3.21875l13.15625,13.125l2.8125-2.8125l-13-13.03125c2.55469-2.97656,4.09375-6.83984,4.09375-11.0625c0-9.37891-7.62109-17-17-17zM21,5c8.29688,0,15,6.70313,15,15c0,8.29688-6.70312,15-15,15c-8.29687,0-15-6.70312-15-15c0-8.29687,6.70313-15,15-15z"
              ></path>
            </g>
          </g>
        </svg>
      </div>

      <img
        class="ml-20 w-8 h-8 text-gray-700"
        width="30"
        height="30"
        src="https://img.icons8.com/ios-glyphs/60/whatsapp.png"
        alt="whatsapp"
      />

      <div class="flex flex-col ml-2">
        <p class="text-xs">WhatsApp SAC</p>
        <p class="text-xs">(47) 99924-2591</p>
      </div>

      <img
        width="30"
        height="30"
        src="https://img.icons8.com/ios-glyphs/30/shopping-cart--v1.png"
        alt="shopping-cart--v1"
        class="ml-20"
      />
      <div class="flex flex-col ml-2">
        <p class="text-xs">Meu</p>
        <p class="text-xs">carrinho</p>
      </div>
    </div>
  </header>

  <main class="pt-32">
    <div class="bg-gray-300 w-full py-24">
      <!-- Quadrado Cinza -->
    </div>

    <div class="bg-white w-full pt-15 flex items-center px-4">
      <img
        width="40"
        height="40"
        src="https://img.icons8.com/ios-glyphs/60/delivery--v1.png"
        alt="delivery--v1"
        class="ml-38"
      />
      <p class="fonte ml-3 text-sm font-semibold">Entrega em todo o Brasil</p>
      <svg
        xmlns="http://www.w3.org/2000/svg"
        x="0px"
        y="0px"
        width="30"
        height="30"
        viewBox="0 0 30 30"
        class="ml-42"
      >
        <path
          d="M 15 1.0996094 C 13.975 1.0996094 12.949922 1.4895313 12.169922 2.2695312 L 7.1894531 7.25 L 7.3398438 7.25 C 8.6098437 7.25 9.7992188 7.740625 10.699219 8.640625 L 14.189453 12.130859 C 14.639453 12.570859 15.360547 12.570859 15.810547 12.130859 L 19.300781 8.640625 C 20.200781 7.740625 21.390156 7.25 22.660156 7.25 L 22.810547 7.25 L 17.830078 2.2695312 C 17.050078 1.4895313 16.025 1.0996094 15 1.0996094 z M 5.6894531 8.75 L 2.2695312 12.169922 C 0.70953125 13.729922 0.70953125 16.270078 2.2695312 17.830078 L 5.6894531 21.25 L 7.3398438 21.25 C 8.2098438 21.25 9.030625 20.910781 9.640625 20.300781 L 13.130859 16.810547 C 14.160859 15.780547 15.839141 15.780547 16.869141 16.810547 L 20.359375 20.300781 C 20.969375 20.910781 21.790156 21.25 22.660156 21.25 L 24.310547 21.25 L 27.730469 17.830078 C 29.290469 16.270078 29.290469 13.729922 27.730469 12.169922 L 24.310547 8.75 L 22.660156 8.75 C 21.790156 8.75 20.969375 9.0892188 20.359375 9.6992188 L 16.869141 13.189453 C 16.359141 13.699453 15.68 13.960938 15 13.960938 C 14.32 13.960938 13.640859 13.699453 13.130859 13.189453 L 9.640625 9.6992188 C 9.030625 9.0892187 8.2098437 8.75 7.3398438 8.75 L 5.6894531 8.75 z M 15 17.539062 C 14.7075 17.539062 14.414453 17.649141 14.189453 17.869141 L 10.699219 21.359375 C 9.7992188 22.259375 8.6098437 22.75 7.3398438 22.75 L 7.1894531 22.75 L 12.169922 27.730469 C 13.729922 29.290469 16.270078 29.290469 17.830078 27.730469 L 22.810547 22.75 L 22.660156 22.75 C 21.390156 22.75 20.200781 22.259375 19.300781 21.359375 L 15.810547 17.869141 C 15.585547 17.649141 15.2925 17.539062 15 17.539062 z"
        ></path>
      </svg>
      <p class="fonte ml-3 text-sm font-semibold">Pague no Pix ou Boleto</p>
      <img
        width="40"
        height="40"
        src="https://img.icons8.com/ios-glyphs/60/bank-card-back-side.png"
        alt="bank-card-back-side"
        class="ml-42"
      />
      <p class="fonte ml-3 text-sm font-semibold">Em até 3x sem juros</p>
    </div>

    <div class="bg-white w-full h-[500px] flex items-center justify-center">
      <div class="flex justify-between gap-24 w-10/12">
        <!-- Primeiro container -->
        <div class="bg-gray-300 p-6 rounded-xl shadow-md flex-1 py-32"></div>

        <!-- Segundo container -->
        <div class="bg-gray-300 p-6 rounded-xl shadow-md flex-1 py-32"></div>
      </div>
    </div>
  </main>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Italianno&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Montserrat:ital,wght@0,100..900;1,100..900&display=swap');

.nome {
  font-family: Italianno, serif;
}

.fonte {
  font-family: Montserrat, sans-serif;
}
</style>
