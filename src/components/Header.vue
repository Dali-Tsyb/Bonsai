<script setup>
import Cart from "./Cart.vue";

defineProps({
   isSearchVisible: Boolean,
   onChangeSearchInput: Function,
   handleSearchClick: {
      type: Function,
      required: true,
   },
   totalItems: Number,
});
</script>

<template>
   <header class="header">
      <div class="header-logo">БОНСАЙ.РФ</div>
      <ul class="header-menu">
         <div class="input-container" :class="{ show: isSearchVisible }">
            <input
               @input="onChangeSearchInput"
               placeholder="Найти товар..."
               type="text"
            />
         </div>
         <li class="header-menu-search">
            <img
               @click="handleSearchClick"
               src="/icons/search.png"
               alt="search"
               title="Поиск товара"
            />
         </li>
         <li class="header-menu-profile">
            <img src="/icons/profile.png" alt="profile" title="Профиль" />
         </li>
         <li class="header-menu-cart">
            <div class="total-items" v-if="totalItems > 0">
               <span>{{ totalItems }}</span>
            </div>
            <img src="/icons/cart.png" alt="cart" />
            <Cart class="cart" />
         </li>
         <li class="header-menu-sidebar">
            <img src="/icons/menu.png" alt="menu" />
            <ul class="drop-menu">
               <li class="drop-menu-history">ИСТОРИЯ</li>
               <li class="drop-menu-club">КЛУБ</li>
               <li class="drop-menu-delivery">ДОСТАВКА</li>
               <li class="drop-menu-stores">МАГАЗИНЫ</li>
            </ul>
         </li>
      </ul>
   </header>
</template>

<style scoped>
header {
   height: fit-content;
   z-index: 100;
   background-color: rgb(237, 237, 237);
   box-shadow: 0 0 13px rgba(99, 99, 99, 0.201);
   display: flex;
   justify-content: space-between;
   align-items: center;
   padding: 0.5vw 1vw;
}
header img {
   width: 1.8vw;
   cursor: pointer;
   opacity: 65%;
}
.header-logo {
   font-family: "yeseva one";
   font-size: 2vw;
   cursor: pointer;
   color: rgb(74, 74, 74);
}
.header-menu {
   display: flex;
   align-items: center;
   gap: 1.5vw;
}
input {
   padding: 0.2vw 0.4vw;
   border: 1px solid rgba(0, 0, 0, 0.379);
   background: rgba(255, 255, 255, 0.686);
   font-size: 1.1vw;
   width: 25vw;
   color: rgba(0, 0, 0, 0.845);
}
.input-container {
   opacity: 0;
   transition: opacity 0.2s;
}
.input-container.show {
   opacity: 1;
}
input:focus {
   outline: none;
   border: 1px solid rgba(0, 0, 0, 0.535);
}
.cart {
   position: absolute;
   top: 2vw;
   right: -3vw;
   opacity: 0;
   pointer-events: none;
   transition: all 0.2s;
}
.header-menu-cart:hover .cart,
.cart:hover {
   opacity: 1;
   pointer-events: all;
}
.header-menu-cart {
   position: relative;
}
.total-items {
   position: absolute;
   z-index: 201;
   right: -0.8vw;
   top: -0.3vw;
   background: rgb(255, 44, 58);
   border-radius: 100px;
   width: 1.3vw;
   height: 1.3vw;
   display: flex;
   align-items: start;
   justify-content: center;
}
.total-items span {
   font-size: 0.9vw;
   color: white;
   font-weight: 600;
}
.drop-menu {
   z-index: 300;
   position: absolute;
   top: 2.6vw;
   right: 0;
   background-color: rgb(237, 237, 237);
   opacity: 0;
   padding: 1vw;
   height: fit-content;
   width: fit-content;
   transition: opacity 0.2s;
   pointer-events: none;
   display: flex;
   flex-direction: column;
   text-align: right;
}
.header-menu-sidebar:hover .drop-menu,
.drop-menu:hover {
   opacity: 1;
   pointer-events: all;
}
.drop-menu li {
   font-size: 1.2vw;
   border-bottom: 1px solid rgba(0, 0, 0, 0.104);
   padding: 0.5vw;
   transition: all 0.1s;
   cursor: pointer;
}
.drop-menu-history {
   border-top: 1px solid rgba(0, 0, 0, 0.104);
}
.drop-menu li:hover {
   background: rgba(255, 255, 255, 0.527);
   scale: 105%;
}
.drop-menu li:active {
   background: rgb(195, 195, 195);
}
@media (width < 800px) {
   header {
      padding: 0.8vw 1.2vw;
   }
   header img {
      width: 2.4vw;
   }
   .header-menu {
      gap: 2.4vw;
   }
   input {
      font-size: 1.5vw;
      width: 35vw;
   }
   .cart {
      top: 2.6vw;
      right: -4.5vw;
   }
   .drop-menu {
      top: 3.4vw;
   }
   .drop-menu li {
      font-size: 1.5vw;
   }
}
@media (width < 550px) {
   header {
      padding: 2.5vw 3vw;
   }
   header img {
      width: 4.8vw;
   }
   .header-logo {
      font-size: 4.5vw;
   }
   input {
      font-size: 3.2vw;
      width: 100%;
   }
   .input-container {
      position: absolute;
      right: 0;
      top: 8vw;
      width: 100%;
      background:  rgba(237, 237, 237);
      padding: 3vw;
   }
   .header-menu {
      gap: 4vw;
   }
   .total-items {
      width: 4vw;
      height: 4vw;
      right: -2.4vw;
      top: -1.5vw;
   }
   .total-items span {
      font-size: 3vw;
   }
   .cart {
      top: 7vw;
      right: -6vw;
   }
   .drop-menu {
      padding: 3vw;
      top: 7vw;
   }
   .drop-menu li {
      font-size: 4vw;
      padding: 2vw;
   }
}
</style>
