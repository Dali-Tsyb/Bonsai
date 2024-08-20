<script setup>
import { inject } from "vue";

const { cart, removeFromCart } = inject("cart");
</script>

<template>
   <section v-auto-animate>
      <div class="cart-list" v-for="item in cart" :key="item.id">
         <img :src="item.img" alt="" />
         <div class="name">{{ item.type }} "{{ item.name }}"</div>
         <div class="price">{{ item.price }} руб.</div>
         <img
            @click="removeFromCart(item)"
            src="/icons/cross.png"
            alt=""
            class="button"
         />
      </div>
   </section>
</template>

<style scoped>
.cart-list {
   display: grid;
   grid-template-areas:
      "photo name button"
      "photo price button";
   grid-template-rows: 1fr;
   gap: 0 1.4vw;
   margin-top: 1vw;
   justify-content: left;
   align-items: stretch;
   border-bottom: 1px solid rgba(0, 0, 0, 0.087);
   padding-bottom: 1vw;
   width: 100%;
}
img {
   grid-area: photo;
   width: 5vw;
}
.name {
   grid-area: name;
   font-size: 1.1vw;
   font-weight: 500;
}
.price {
   grid-area: price;
   font-size: 1.1vw;
   font-weight: 600;
}
.button {
   grid-area: button;
   width: 1vw;
   align-self: end;
   justify-self: flex-end;
   opacity: 0.65;
   cursor: pointer;
   transition: opacity 0.2s;
}
.button:hover {
   opacity: 1;
}
@media (width < 800px) {
   .cart-list {
      padding-bottom: 2vw;
   }
   img {
      width: 6vw;
   }
   .name {
      font-size: 1.3vw;
   }
   .price {
      font-size: 1.4vw;
   }
   .button {
      width: 1.3vw;
   }
}
@media (width < 550px) {
   .cart-list {
      gap: 0 3vw;
      margin-top: 5vw;
      padding-bottom: 4vw;
   }
   img {
      width: 15vw;
   }
   .name {
      font-size: 3.6vw;
   }
   .price {
      font-size: 4vw;
   }
   .button {
      width: 3vw;
   }
}
 </style>
