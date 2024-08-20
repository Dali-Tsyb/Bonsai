<script setup>
import { inject } from "vue";
import CartList from "./CartList.vue";

const { totalPrice } = inject("cart");
</script>

<template>
   <div class="cart">
      <div class="cart-title">КОРЗИНА</div>
      <div class="cart-body" v-if="totalPrice > 0">
         <CartList />
         <div class="cart-total">
            <span>Итого:</span><span>{{ totalPrice }} руб.</span>
         </div>
      </div>
      <div class="cart-empty" v-if="totalPrice === 0">
         <img src="/icons/bonsai.png" alt="">
         <p>ПУСТО :(</p>
      </div>
      <div class="cart-button" v-if="totalPrice > 0">ПЕРЕЙТИ В КОРЗИНУ</div>
   </div>
</template>

<style scoped>
.cart {
   background-color: rgb(237, 237, 237);
   border-radius: 0 0 20px 20px;
   width: 23vw;
   box-shadow: 0 15px 13px rgba(99, 99, 99, 0.201);
   padding-top: 2vw;
}
.cart-title {
   font-size: 1.3vw;
   font-weight: 500;
   text-align: center;
}
.cart-body {
   margin: 2vw 2vw 1vw 2vw;
}
.cart-total {
   margin-top: 2vw;
   display: flex;
   justify-content: space-between;
}
.cart-total span {
   font-size: 1.2vw;
   font-weight: 600;
}
.cart-button {
   font-size: 1vw;
   letter-spacing: 0.07vw;
   color: rgba(255, 255, 255, 0.968);
   text-align: center;
   background-color: rgb(112, 138, 112);
   border-radius: 0 0 20px 20px;
   padding: 1vw 2vw;
   cursor: pointer;
   transition: background 0.2s;
}
.cart-button:hover {
   background: rgb(140, 169, 140);
}
.cart-button:active {
   background: rgb(112, 138, 112);
}
.cart-empty {
   display: flex;
   flex-direction: column;
   align-items: center;
   justify-content: center;
   margin: 3vw 0;
   gap: 2vw;
}
.cart-empty img {
   width: 6vw;
   opacity: 0.2;
}
.cart-empty p {
   font-size: 1.3vw;
   font-weight: 500;
   opacity: 0.3;
}
@media (width < 800px) {
   .cart {
      width: 27vw;
   }
   .cart-title {
      font-size: 2vw;
   }
   .cart-total span {
      font-size: 1.5vw;
   }
   .cart-button {
      font-size: 1.5vw;
      padding: 1.6vw 2vw;
   }
}
@media (width < 550px) {
   .cart {
      width: 70vw;
   }
   .cart-title {
      font-size: 5vw;
   }
   .cart-body {
      margin: 4vw;
   }
   .cart-total span {
      font-size: 4vw;
   }
   .cart-button {
      font-size: 4vw;
      padding: 3vw 4vw;
   }
   .cart-empty {
      gap: 4vw;
      margin: 10vw 0;
   }
   .cart-empty img {
      width: 20vw;
   }
   .cart-empty p {
      font-size: 4vw;
   }
}
</style>
