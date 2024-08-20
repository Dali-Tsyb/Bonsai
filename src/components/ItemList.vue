<script setup>
import { inject } from "vue";

const items = inject("items");

const { addToCart, isAdded } = inject("cart");
</script>

<template>
   <div class="container" v-auto-animate>
      <div v-for="item in items" :key="item.id" class="item_card">
         <div class="upper">
            <div class="img"><img :src="item.img" alt="item" /></div>
            <div class="name">{{ item.type }} "{{ item.name }}"</div>
            <div class="height">Высота: {{ item.height }} см</div>
            <div class="age">Возраст: {{ item.age }} лет</div>
         </div>
         <div class="lower">
            <div class="price">{{ item.price }} руб.</div>
            <div
               @click="addToCart(item)"
               class="button"
               :style="{ pointerEvents: isAdded[item.id] ? 'none' : 'auto' }"
            >
               {{ isAdded[item.id] ? "ДОБАВЛЕНО!" : "ДОБАВИТЬ В КОРЗИНУ" }}
            </div>
         </div>
      </div>
   </div>
</template>

<style scoped>
.container {
   z-index: 2;
   position: relative;
   margin-top: 4vw;
   width: 100%;
   display: grid;
   grid-template-columns: repeat(4, 1fr);
   gap: 1vw;
   justify-content: stretch;
}
.item_card {
   border-radius: 20px;
   background: rgb(245, 245, 245);
   box-shadow: 0 0 13px rgba(99, 99, 99, 0.135);
   cursor: pointer;
   transition: scale 0.2s;
   display: flex;
   flex-direction: column;
   justify-content: space-between;
   overflow: visible;
   height: 100%;
}
.item_card:hover {
   scale: 105%;
   border-radius: 20px 20px 0 0;
}
.img {
   display: flex;
   justify-content: center;
   overflow: hidden;
}
img {
   height: 100%;
   width: 100%;
   object-fit: cover;
}
.upper {
   padding: 2vw 2vw 0 2vw;
}
.name {
   font-size: 1.2vw;
   font-weight: 600;
   margin: 2vw 0 1vw 0;
}
.age,
.height {
   color: rgba(0, 0, 0, 0.439);
   font-size: 0.9vw;
   font-weight: 500;
}
.price {
   align-self: end;
   margin: 1vw 2vw 1.5vw 2vw;
   font-size: 1.5vw;
   font-weight: 600;
}
.button {
   z-index: 100;
   position: absolute;
   bottom: -3vw;
   display: none;
   width: 100%;
   justify-self: center;
   padding: 1.2vw;
   text-align: center;
   background: rgb(112, 138, 112);
   border-radius: 0 0 20px 20px;
   box-shadow: 0 8px 15px rgba(105, 105, 105, 0.4);
   font-size: 1.2vw;
   font-weight: 500;
   color: rgb(245, 245, 245);
   transition: background 0.2s;
}
.button:hover {
   background: rgb(140, 169, 140);
}
.button:active {
   background: rgb(112, 138, 112);
}
.item_card:hover .button {
   display: block;
}
@media (width < 800px) {
   .container {
      grid-template-columns: repeat(3, 1fr);
      gap: 1.5vw;
   }
   .upper {
      padding: 2.3vw 2.3vw 0 2.3vw;
   }
   .name {
      font-size: 1.5vw;
   }
   .age,
   .height {
      font-size: 1.2vw;
   }
   .price {
      font-size: 1.8vw;
      margin: 1.3vw 2.3vw 2.3vw 2.3vw;
   }
   .button {
      font-size: 1.5vw;
   }
}
@media (width < 550px) {
   .container {
      grid-template-columns: repeat(2, 1fr);
      gap: 3vw;
   }
   .upper {
      padding: 4vw 4vw 0 4vw;
   }
   .name {
      font-size: 2.8vw;
      margin: 4vw 0 3vw 0;
   }
   .age,
   .height {
      font-size: 2.1vw;
   }
   .price {
      font-size: 4vw;
      margin: 3vw 5vw 4vw 4vw;
   }
   .button {
      font-size: 3vw;
      padding: 2vw 0;
      bottom: -4.6vw;
   }
}
@media (width < 400px) {
   .container {
      grid-template-columns: repeat(1, 1fr);
      margin-top: 8vw;
      gap: 5vw;
   }
   .upper {
      padding: 6vw 6vw 0 6vw;
   }
   .name {
      font-size: 4vw;
      margin: 5vw 0 4vw 0;
   }
   .age,
   .height {
      font-size: 3vw;
   }
   .price {
      font-size: 5vw;
      margin: 4vw 6vw 5vw 6vw;
   }
   .button {
      font-size: 3.6vw;
      padding: 3vw 0;
      bottom: -7vw;
   }
}
</style>
