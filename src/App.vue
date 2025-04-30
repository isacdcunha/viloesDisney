<script setup>
import { ref, computed } from 'vue'

const query = ref('')

const perfumes = ref([
  {
    id: 1,
    nome: 'Queen of Hearts',
    imagem: 'https://bluebus-wp.s3.amazonaws.com/wp-content/uploads/2014/01/perfume-queens.jpg',
    preco: 'R$ 399,90',
  },
  {
    id: 2,
    nome: 'Cruella de Vil',
    imagem: 'https://bluebus-wp.s3.amazonaws.com/wp-content/uploads/2014/01/perfume-cruella.jpg',
    preco: 'R$ 399,90',
  },
  {
    id: 3,
    nome: 'The Evil Queen',
    imagem: 'https://i.pinimg.com/originals/cf/fb/f7/cffbf773ae092465590494b6de27afac.jpg',
    preco: 'R$ 489,90',
  },
  {
    id: 4,
    nome: 'Doctor Facilier',
    imagem:
      'https://hilnethcorreia.com.br/wp-content/uploads/2019/06/perfumes-viloes-disney-28.jpg',
    preco: 'R$ 259,90',
  },
  {
    id: 5,
    nome: 'Gaston',
    imagem:
      'https://hilnethcorreia.com.br/wp-content/uploads/2019/06/perfumes-viloes-disney-21.jpg',
    preco: 'R$ 249,90',
  },
  {
    id: 6,
    nome: 'Hades',
    imagem:
      'https://hilnethcorreia.com.br/wp-content/uploads/2019/06/perfumes-viloes-disney-18.jpg',
    preco: 'R$ 329,90',
  },
  {
    id: 7,
    nome: 'Mother Gothel',
    imagem:
      'https://hilnethcorreia.com.br/wp-content/uploads/2019/06/perfumes-viloes-disney-17.jpg',
    preco: 'R$ 299,90',
  },
  {
    id: 8,
    nome: 'Maleficent',
    imagem:
      'https://hilnethcorreia.com.br/wp-content/uploads/2019/06/perfumes-viloes-disney-19.jpg',
    preco: 'R$ 399,90',
  },
  {
    id: 9,
    nome: 'Ursula',
    imagem:
      'https://hilnethcorreia.com.br/wp-content/uploads/2019/06/perfumes-viloes-disney-30.jpg',
    preco: 'R$ 259,90',
  },
  {
    id: 10,
    nome: 'Scar',
    imagem:
      'https://hilnethcorreia.com.br/wp-content/uploads/2019/06/perfumes-viloes-disney-26.jpg',
    preco: 'R$ 199,90',
  },
  {
    id: 11,
    nome: 'Jafar',
    imagem:
      'https://hilnethcorreia.com.br/wp-content/uploads/2019/06/perfumes-viloes-disney-23.jpg',
    preco: 'R$ 159,90',
  },
  {
    id: 12,
    nome: 'Captain Hook',
    imagem:
      'https://hilnethcorreia.com.br/wp-content/uploads/2019/06/perfumes-viloes-disney-22.jpg',
    preco: 'R$ 189,90',
  },
  {
    id: 13,
    nome: 'Prince John',
    imagem:
      'https://hilnethcorreia.com.br/wp-content/uploads/2019/06/perfumes-viloes-disney-13.jpg',
    preco: 'R$ 229,90',
  },
  {
    id: 14,
    nome: 'Lady Tremaine',
    imagem:
      'https://hilnethcorreia.com.br/wp-content/uploads/2019/06/perfumes-viloes-disney-29.jpg',
    preco: 'R$ 219,50',
  },
])
const vestido13 = computed(() => {
  return perfumes.value.find((item) => item.id === 13)
})
const vestido14 = computed(() => {
  return perfumes.value.find((item) => item.id === 14)
})

const filteredPerfumes = ref([...perfumes.value])

function search() {
  const searchTerm = query.value.trim().toLowerCase()

  if (!searchTerm) {
    filteredPerfumes.value = [...perfumes.value]
  } else {
    filteredPerfumes.value = perfumes.value.filter((perfume) =>
      perfume.nome.toLowerCase().includes(searchTerm),
    )
  }

  const perfumesSection = document.getElementById('perfumes')
  if (perfumesSection) {
    perfumesSection.scrollIntoView({ behavior: 'smooth' })
  }
}
const isMenuOpen = ref(false)
const cart = ref([])
const isCartOpen = ref(false)
const isSearchOpen = ref(false)

function addToCart(perfume) {
  const existingProduct = cart.value.find((item) => item.id === perfume.id)

  if (existingProduct) {
    existingProduct.quantity++
  } else {
    cart.value.push({ ...perfume, quantity: 1 })
  }
}

function addLancamento13(vestido13) {
  const existingProduct = cart.value.find((item) => item.id === vestido13.id)

  if (existingProduct) {
    existingProduct.quantity++
  } else {
    cart.value.push({ ...vestido13, quantity: 1 })
  }
}
function addLancamento14(vestido14) {
  const existingProduct = cart.value.find((item) => item.id === vestido14.id)

  if (existingProduct) {
    existingProduct.quantity++
  } else {
    cart.value.push({ ...vestido14, quantity: 1 })
  }
}

function toggleCart() {
  isCartOpen.value = !isCartOpen.value
}
function toggleMenu() {
  isMenuOpen.value = !isMenuOpen.value
}
function closeSearch() {
  isSearchOpen.value = false
}

const totalPrice = computed(() => {
  return cart.value.reduce((total, item) => {
    const price = parseFloat(item.preco.replace('R$', '').replace(',', '.')) || 0
    return total + price * item.quantity
  }, 0)
})
</script>

<template>
  <header class="fixed top-0 left-0 w-full bg-white shadow-sm z-50">
    <div class="header-all flex items-center justify-around p-4 md:px-10">
      <!-- Logo -->
      <h1 class="text-4xl md:text-6xl titulo">Essência sombria</h1>

      <!-- Barra de pesquisa -->
      <div class="barra-pesquisa relative" :id="isSearchOpen == true ? 'open' : 'fechado'">
        <input
          type="text"
          v-model="query"
          @input="search"
          @keyup.enter="search"
          placeholder="Buscar..."
          class="py-2 pl-4 pr-10 border border-black rounded-md focus:outline-none focus:ring-2 focus:ring-blue-500 w-72"
          :id="isSearchOpen ? 'open' : ''"
        />
        <svg
          class="absolute right-3 top-1/2 transform -translate-y-1/2 text-gray-400 w-5 h-5"
          xmlns="http://www.w3.org/2000/svg"
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

      <!-- Menu desktop -->
      <div class="menu-desktop hidden md:flex items-center space-x-8">
        <!-- Login -->
        <div class="flex items-center">
          <img src="https://img.icons8.com/ios-glyphs/60/user--v1.png" alt="user" class="w-6 h-6" />
          <div class="flex flex-col ml-2 text-xs">
            <p>Olá, visitante!</p>
            <p>Entrar/Cadastrar</p>
          </div>
        </div>

        <!-- WhatsApp -->
        <div class="flex items-center">
          <img
            src="https://img.icons8.com/ios-glyphs/60/whatsapp.png"
            alt="whatsapp"
            class="w-6 h-6"
          />
          <div class="flex flex-col ml-2 text-xs">
            <p>WhatsApp SAC</p>
            <p>(47) 99924-2591</p>
          </div>
        </div>

        <!-- Carrinho -->
        <div class="flex items-center cursor-pointer" @click="toggleCart">
          <img
            width="30"
            height="30"
            src="https://img.icons8.com/ios-glyphs/30/shopping-cart--v1.png"
            alt="carrinho"
          />
          <button class="ml-2 text-sm hover:underline">Meu carrinho</button>
        </div>
      </div>

      <div class="flex gap-5">
        <!-- Search Open Button -->
        <svg
          xmlns="http://www.w3.org/2000/svg"
          @click="isSearchOpen = true"
          class="openSearch cursor-pointer"
          x="0px"
          y="0px"
          width="30"
          height="30"
          viewBox="0 0 50 50"
        >
          <path
            d="M 21 3 C 11.621094 3 4 10.621094 4 20 C 4 29.378906 11.621094 37 21 37 C 24.710938 37 28.140625 35.804688 30.9375 33.78125 L 44.09375 46.90625 L 46.90625 44.09375 L 33.90625 31.0625 C 36.460938 28.085938 38 24.222656 38 20 C 38 10.621094 30.378906 3 21 3 Z M 21 5 C 29.296875 5 36 11.703125 36 20 C 36 28.296875 29.296875 35 21 35 C 12.703125 35 6 28.296875 6 20 C 6 11.703125 12.703125 5 21 5 Z"
          ></path>
        </svg>
        <!-- Menu mobile -->
        <div class="md:hidden relative" id="menu-mobile">
          <button @click="toggleMenu" class="focus:outline-none cursor-pointer">
            <svg class="w-8 h-8" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="2"
                d="M4 6h16M4 12h16m-7 6h7"
              ></path>
            </svg>
          </button>
        </div>
        <!-- Dropdown -->
        <div
          v-if="isMenuOpen"
          class="absolute right-0 mt-2 w-48 bg-white border rounded-md shadow-lg py-2 z-50"
        >
          <div class="flex w-full justify-end pr-2 mb-2">
            <button
              @click="isMenuOpen = false"
              class="text-gray-500 hover:text-red-600 transition-all duration-300 text-2xl cursor-pointer"
            >
              &times;
            </button>
          </div>
          <a href="#" class="block px-4 py-2 text-sm text-gray-700 hover:bg-gray-100 items-center">
            <img
              src="https://img.icons8.com/ios-glyphs/60/user--v1.png"
              alt="user"
              class="w-5 h-5 mr-2"
            />
            Entrar/Cadastrar
          </a>
          <a href="#" class="block px-4 py-2 text-sm text-gray-700 hover:bg-gray-100 items-center">
            <img
              src="https://img.icons8.com/ios-glyphs/60/whatsapp.png"
              alt="whatsapp"
              class="w-5 h-5 mr-2"
            />
            WhatsApp SAC
          </a>
          <a
            href="#"
            @click="toggleCart"
            class="block px-4 py-2 text-sm text-gray-700 hover:bg-gray-100 items-center"
          >
            <img
              width="24"
              height="24"
              src="https://img.icons8.com/ios-glyphs/30/shopping-cart--v1.png"
              alt="carrinho"
              class="mr-2"
            />
            Meu carrinho
          </a>
        </div>
      </div>
    </div>
  </header>
  <main @click="closeSearch" class="main-content">
    <div class="imagem-principal w-full">
      <img
        src="https://wallpapers.com/images/hd/disney-villain-movie-maleficent-er52qk0hsvft2alj.jpg"
        alt=""
      />
    </div>

    <div class="beneficios-content bg-white w-full pt-20 flex-wrap flex justify-around px-4">
      <div class="beneficios flex justify-around w-full flex-wrap">
        <div class="flex items-center">
          <img
            width="40"
            height="40"
            src="https://img.icons8.com/ios-glyphs/60/delivery--v1.png"
            alt="delivery--v1"
            class=""
          />
          <p class="fonte ml-3 text-sm font-semibold">Entrega em todo o Brasil</p>
        </div>
        <div class="flex items-center">
          <svg
            xmlns="http://www.w3.org/2000/svg"
            x="0px"
            y="0px"
            width="30"
            height="30"
            viewBox="0 0 30 30"
            class=""
          >
            <path
              d="M 15 1.0996094 C 13.975 1.0996094 12.949922 1.4895313 12.169922 2.2695312 L 7.1894531 7.25 L 7.3398438 7.25 C 8.6098437 7.25 9.7992188 7.740625 10.699219 8.640625 L 14.189453 12.130859 C 14.639453 12.570859 15.360547 12.570859 15.810547 12.130859 L 19.300781 8.640625 C 20.200781 7.740625 21.390156 7.25 22.660156 7.25 L 22.810547 7.25 L 17.830078 2.2695312 C 17.050078 1.4895313 16.025 1.0996094 15 1.0996094 z M 5.6894531 8.75 L 2.2695312 12.169922 C 0.70953125 13.729922 0.70953125 16.270078 2.2695312 17.830078 L 5.6894531 21.25 L 7.3398438 21.25 C 8.2098438 21.25 9.030625 20.910781 9.640625 20.300781 L 13.130859 16.810547 C 14.160859 15.780547 15.839141 15.780547 16.869141 16.810547 L 20.359375 20.300781 C 20.969375 20.910781 21.790156 21.25 22.660156 21.25 L 24.310547 21.25 L 27.730469 17.830078 C 29.290469 16.270078 29.290469 13.729922 27.730469 12.169922 L 24.310547 8.75 L 22.660156 8.75 C 21.790156 8.75 20.969375 9.0892188 20.359375 9.6992188 L 16.869141 13.189453 C 16.359141 13.699453 15.68 13.960938 15 13.960938 C 14.32 13.960938 13.640859 13.699453 13.130859 13.189453 L 9.640625 9.6992188 C 9.030625 9.0892187 8.2098437 8.75 7.3398438 8.75 L 5.6894531 8.75 z M 15 17.539062 C 14.7075 17.539062 14.414453 17.649141 14.189453 17.869141 L 10.699219 21.359375 C 9.7992188 22.259375 8.6098437 22.75 7.3398438 22.75 L 7.1894531 22.75 L 12.169922 27.730469 C 13.729922 29.290469 16.270078 29.290469 17.830078 27.730469 L 22.810547 22.75 L 22.660156 22.75 C 21.390156 22.75 20.200781 22.259375 19.300781 21.359375 L 15.810547 17.869141 C 15.585547 17.649141 15.2925 17.539062 15 17.539062 z"
            ></path>
          </svg>
          <p class="fonte ml-3 text-sm font-semibold">Pague no Pix ou Boleto</p>
        </div>
        <div class="flex items-center">
          <img
            width="40"
            height="40"
            src="https://img.icons8.com/ios-glyphs/60/bank-card-back-side.png"
            alt="bank-card-back-side"
            class=""
          />
          <p class="fonte ml-3 text-sm font-semibold">Em até 3x sem juros</p>
        </div>
      </div>
    </div>

    <div class="bg-white w-full h-auto flex mt-15 flex-col items-center pb-20 justify-center">
      <h2 class="titulo flex item-center text-5xl pt-5 pb-2">Lançamentos</h2>
      <div class="flex justify-around flex-wrap gap-24 w-full">
        <!-- Primeiro container -->
        <div class="box-cinza flex justify-center items-center p-6 rounded-xl">
          <div class="lancamento flex flex-col items-center text-center">
            <img :src="vestido13.imagem" alt="" class="w-full h-auto object-cover rounded-md" />
            <h2 class="text-lg font-bold mt-4 fonte">{{ vestido13.nome }}</h2>
            <p class="text-gray-500 font-semibold fonte">{{ vestido13.preco }}</p>
            <div class="items-center text-center">
              <button
                @click="addLancamento13(vestido13)"
                class="relative fonte mt-2 bg-black text-white py-2 px-4 rounded-lg overflow-hidden group hover:rounded-none transition-all duration-700 cursor-pointer"
              >
                Adicionar ao carrinho
                <span
                  class="absolute bottom-1 mb-1 left-0 w-full h-[1px] bg-white transform scale-x-0 group-hover:scale-x-[0.9] transition-all duration-500"
                ></span>
              </button>
            </div>
          </div>
        </div>

        <!-- Segundo container -->
        <div class="box-cinza flex justify-center items-center p-6 rounded-xl">
          <div class="lancamento flex flex-col items-center text-center">
            <img :src="vestido14.imagem" alt="" class="w-full h-auto object-cover rounded-md" />
            <h2 class="text-lg font-bold mt-4 fonte">{{ vestido14.nome }}</h2>
            <p class="text-gray-500 font-semibold fonte">{{ vestido14.preco }}</p>
            <div class="items-center text-center">
              <button
                @click="addLancamento14(vestido14)"
                class="relative fonte mt-2 bg-black text-white py-2 px-4 rounded-lg overflow-hidden group hover:rounded-none transition-all duration-700 cursor-pointer"
              >
                Adicionar ao carrinho
                <span
                  class="absolute bottom-1 mb-1 left-0 w-full h-[1px] bg-white transform scale-x-0 group-hover:scale-x-[0.9] transition-all duration-500"
                ></span>
              </button>
            </div>
          </div>
        </div>
      </div>
    </div>

    <div class="w-full h-10 bg-white flex items-center px-4 flex-col">
      <h2 class="titulo flex item-center text-5xl">Encontre o seu cheiro</h2>
      <p class="fonte text-md">Exale o charme sombrio dos vilões da Disney!</p>
    </div>

    <div class="bg-white flex items-center w-full mt-20 justify-center mb-20" id="perfumes">
      <div class="flex flex-wrap gap-x-40 gap-y-15 justify-center">
        <div v-if="filteredPerfumes.length === 0" class="w-full text-center text-lg text-gray-500">
          <p>Nenhum perfume encontrado</p>
        </div>

        <div
          v-for="perfume in filteredPerfumes"
          :key="perfume.id"
          class="bg-white p-4 rounded-lg w-64"
        >
          <div class="flex flex-col items-center text-center">
            <img :src="perfume.imagem" alt="" class="w-full h-56 object-cover rounded-md" />
            <h2 class="text-lg font-bold mt-4 fonte">{{ perfume.nome }}</h2>
            <p class="text-gray-500 font-semibold fonte">{{ perfume.preco }}</p>
          </div>

          <div class="items-center text-center">
            <button
              @click="addToCart(perfume)"
              class="relative fonte mt-2 bg-black text-white py-2 px-4 rounded-lg overflow-hidden group hover:rounded-none transition-all duration-700 cursor-pointer"
            >
              Adicionar ao carrinho
              <span
                class="absolute bottom-1 mb-1 left-0 w-full h-[1px] bg-white transform scale-x-0 group-hover:scale-x-[0.9] transition-all duration-500"
              ></span>
            </button>
          </div>
        </div>
      </div>
    </div>

    <div
      v-if="isCartOpen"
      class="fixed top-32 right-5 w-80 bg-white border rounded-lg shadow-lg p-4 z-50"
    >
      <div class="flex justify-between items-center mb-4">
        <h2 class="text-xl font-bold fonte">Meu Carrinho</h2>
        <button
          @click="toggleCart"
          class="text-gray-500 hover:text-red-600 transition-all duration-300 text-2xl cursor-pointer"
        >
          &times;
        </button>
      </div>

      <div v-if="cart.length === 0" class="text-gray-500 fonte">Carrinho vazio</div>

      <div v-else>
        <div v-for="item in cart" :key="item.id" class="flex justify-between items-center mb-2">
          <div>
            <p class="font-semibold fonte">{{ item.nome }}</p>
            <p class="text-sm text-gray-500 fonte">Qtd: {{ item.quantity }}</p>
          </div>
          <p class="font-semibold fonte">{{ item.preco }}</p>
        </div>

        <div class="mt-4 border-t pt-2 flex justify-between">
          <span class="font-semibold fonte">Total:</span>
          <span class="font-semibold fonte">R$ {{ totalPrice.toFixed(2).replace('.', ',') }}</span>
        </div>

        <button
          class="mt-4 w-full bg-black text-white py-2 rounded fonte font-semibold hover:bg-red-700 transition-all duration-300 cursor-pointer"
          @click="cart = []"
        >
          Limpar Carrinho
        </button>
      </div>
    </div>
  </main>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Italianno&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Montserrat:ital,wght@0,100..900;1,100..900&display=swap');

.titulo {
  font-family: Italianno, serif;
}

.fonte {
  font-family: Montserrat, sans-serif;
}

.imagem-principal {
  margin-top: -7vw;
}

.main-content {
  margin-top: 93px;
}

.head {
  width: 100vw;
}

.head img {
  width: 30px;
  height: 30px;
}

.barra-pesquisa input {
  width: 30vw;
}

.barra-pesquisa {
  transition: 0.2s all ease;
}

#open {
  display: block;
}

.openSearch {
  display: none;
}

.box-cinza {
  width: 500px;
  height: 500px;
  cursor: pointer;
  transition: transform 0.3s ease;
}

.box-cinza:hover {
  border: 2px solid gray;
  transform: scale(1.05);
  transition: transform 0.3s ease;
}

@media (max-width: 1200px) {
  .textos {
    display: none;
  }
}

@media (max-width: 1160px) {
  .menu-desktop button {
    display: none;
  }

  .menu-desktop p {
    display: none;
  }
}

@media (max-width: 767px) {
  #menu-mobile button {
    display: block;
  }

  .main-content {
    margin-top: 72px;
  }

  .barra-pesquisa input {
    height: 30px;
  }

  .header-all {
    justify-content: space-between;
  }
}

@media (max-width: 470px) {
  .barra-pesquisa,
  .barra-pesquisa input {
    position: absolute;
    width: 93vw;
    height: 40px;
    background-color: white;
    z-index: 10;
    display: none;
    justify-self: center;
    margin-left: -5px;
  }

  .barra-pesquisa svg {
    display: none;
  }

  .openSearch {
    display: block;
  }
}

@media (max-width: 470px) {
  .barra-pesquisa,
  .barra-pesquisa input {
    position: absolute;
    width: 93vw;
    height: 40px;
    background-color: white;
    z-index: 10;
    display: none;
    justify-self: center;
    margin-left: -5px;
  }

  .barra-pesquisa svg {
    display: none;
  }

  .openSearch {
    display: block;
  }
}

@media (max-width: 454px) {
  .beneficios {
    height: 10rem;
    gap: 10px;
    padding-top: 20px;
  }
  .beneficios-content {
    padding-top: 15px;
  }
}
</style>
