<script setup>
import { ref, reactive, onMounted, provide, watch, computed } from "vue";
import axios from "axios";

import Header from "./components/Header.vue";
import Intro from "./components/Intro.vue";
import Catalogue from "./components/Catalogue.vue";
import About from "./components/About.vue";
import Footer from "./components/Footer.vue";

const items = ref([]);
const meta = reactive({
   total_pages: 0,
   current_page: 1,
   per_page: 16,
});
const cart = ref([]);
const filters = reactive({
   sortBy: "",
   searchQuery: "",
});
const catalogue = ref();
const isSearchVisible = ref(false);

// SEARCH //
function handleSearchClick() {
   isSearchVisible.value = !isSearchVisible.value;
   window.scrollTo({
      top: catalogue.value.$el.offsetTop,
      behavior: "smooth",
   });
}
const onChangeSearchInput = (e) => {
   filters.searchQuery = e.target.value;
};
//

// SORTING //
const selectedOption = ref({});
const showDropdown = ref(false);
const options = [
   { value: "price", text: "Цена (по возрастанию)" },
   { value: "-price", text: "Цена (по убыванию)" },
   { value: "popularity", text: "Популярность (по возрастанию)" },
   { value: "-popularity", text: "Популярность (по убыванию)" },
];

function toggleDropdown() {
   showDropdown.value = !showDropdown.value;
}
function selectOption(option) {
   selectedOption.value = option;
   showDropdown.value = false;
   filters.sortBy = option.value;
}
//

// PAGINATION //
const nextPage = () => {
   if (meta) {
      meta.current_page += 1;
      fetchData();
   }
};

const prevPage = () => {
   if (meta) {
      meta.current_page -= 1;
      fetchData();
   }
};

const isFirstPage = computed(() => meta.current_page === 1);
const isLastPage = computed(() => meta.current_page === meta.total_pages);
//

// CART //
const isAdded = ref({});
const totalPrice = ref(0);
const totalItems = ref(0);

function addToCart(item) {
   cart.value.push(item);
   totalPrice.value += item.price;
   totalItems.value++;
   isAdded.value[item.id] = true;
}
function removeFromCart(item) {
   cart.value.splice(cart.value.indexOf(item), 1);
   totalPrice.value -= item.price;
   totalItems.value--;
   isAdded.value[item.id] = false;
}
//

async function fetchData() {
   try {
      const params = {};

      if (filters.searchQuery) {
         params.type = `*${filters.searchQuery}*`;
      }

      if (filters.sortBy) {
         params.sortBy = `${filters.sortBy}`;
      }

      params.page = meta.current_page;
      params.limit = meta.per_page;

      const { data } = await axios.get(
         "https://7cb69a3f0249c4a6.mokky.dev/items",
         { params }
      );
      items.value = data.items;
      meta.total_pages = data.meta.total_pages;
      meta.current_page = data.meta.current_page;
   } catch (err) {
      console.log(err);
   }
}

watch(filters, fetchData);

onMounted(fetchData);
provide("items", items);
provide("cart", { cart, addToCart, removeFromCart, totalPrice, isAdded });
</script>

<template>
   <section>
      <Header
         :isSearchVisible="isSearchVisible"
         :onChangeSearchInput="onChangeSearchInput"
         :handleSearchClick="handleSearchClick"
         :totalItems="totalItems"
      />
      <Intro />
   </section>
   <ul class="intro-text-specials">
      <li class="intro-specials-gift">
         <img class="gift" src="/icons/gift.png" alt="gift" />
         <h6>Вам в подарок</h6>
         <p>Статуэтка, удобрение, упаковка, описание и клубная карта</p>
      </li>
      <li class="intro-specials-delivery">
         <img class="delivery" src="/icons/delivery.png" alt="delivery" />
         <h6>Доставка</h6>
         <p>Бесплатно по Москве и Петербургу за час, по России 2 дня</p>
      </li>
      <li class="intro-specials-card">
         <img class="card" src="/icons/card.png" alt="card" />
         <h6>Клубная система</h6>
         <p>
            Бесплатно: стрижка Вашего дерева, снабжение удобрениями, гостиница
            для бонсай
         </p>
      </li>
   </ul>
   <Catalogue
      :selectOption="selectOption"
      :showDropdown="showDropdown"
      :toggleDropdown="toggleDropdown"
      :selectedOption="selectedOption"
      :options="options"
      :nextPage="nextPage"
      :prevPage="prevPage"
      :isFirstPage="isFirstPage"
      :isLastPage="isLastPage"
      ref="catalogue"
   />
   <About />
   <Footer />
</template>

<style scoped>
section {
   height: 100vh;
   display: flex;
   flex-direction: column;
}
Header {
   position: fixed;
   width: 100%;
   top: 0;
}
.intro-text-specials {
   display: none;
   margin: 0 3vw 4vw 3vw;
   background: rgba(255, 255, 255, 0.787);
   backdrop-filter: blur(8px);
   border-radius: 40px;
   box-shadow: 0 0 13px rgba(255, 255, 255, 0.461);
   padding: 10vw 8vw;
   flex-direction: column;
   align-items: center;
   justify-content: center;
   gap: 6vw;
   text-align: left;
}
li {
   opacity: 0.8;
   display: grid;
   grid-template-areas:
      "icon title"
      "icon text";
   grid-template-columns: 15% 75%;
   align-items: center;
   gap: 1vw 5vw;
   flex: 0 0 0;
}
.gift,
.delivery,
.card {
   opacity: 65%;
   width: 100%;
   grid-area: icon;
}
.gift,
.delivery {
   filter: invert(1);
}
h6 {
   grid-area: title;
   font-size: calc(10px + 0.25vw);
   font-weight: 600;
   text-transform: uppercase;
}
p {
   grid-area: text;
   font-size: calc(10px + 0.25vw);
}
@media (width < 550px) {
   .intro-text-specials {
      display: flex;
   }
}
</style>
