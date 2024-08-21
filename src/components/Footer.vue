<script setup>
function scrollToTop() {
   window.scrollTo({ top: 0, behavior: "smooth" });
}
</script>

<template>
   <footer>
      <div class="top">
         <div class="company">
            <div>
               <h6>КОМПАНИЯ</h6>
               <div>О клубе</div>
               <div>Блог</div>
            </div>
         </div>
         <div class="info">
            <div>
               <h6>ИНФОРМАЦИЯ</h6>
               <div>Магазины</div>
               <div>Условия оплаты</div>
               <div>Условия доставки</div>
               <div>Политика</div>
            </div>
         </div>
         <div class="help">
            <div>
               <h6>ПОМОЩЬ</h6>
               <div>Вопрос-ответ</div>
               <div>Контакты</div>
            </div>
         </div>
         <div class="socials">
            <div>
               <h6>МЫ В СОЦСЕТЯХ</h6>
               <div>
                  <img class="vk" src="/icons/vk.png" alt="vk" />
                  <img class="fb" src="/icons/fb.png" alt="fb" />
                  <img class="inst" src="/icons/inst.png" alt="inst" />
                  <img class="tg" src="/icons/tg.png" alt="tg" />
               </div>
            </div>
         </div>
      </div>
      <div class="bottom">
         <div>2024 © ООО «Бонсай Клуб» ОГРН 1077757621809</div>
         <button @click="scrollToTop">
            <img src="/icons/arrow.png" alt="" />
            <span>НАВЕРХ</span>
            <img src="/icons/arrow.png" alt="" />
         </button>
      </div>
   </footer>
</template>

<style scoped>
footer {
   background-color: rgb(237, 237, 237);
   box-shadow: 0 0 13px rgba(255, 255, 255, 0.461);
   padding: 3vw;
   display: flex;
   flex-direction: column;
   gap: 10vw;
}
.top {
   display: flex;
   justify-content: space-between;
}
.top > * {
   border-right: 1px solid rgba(0, 0, 0, 0.175);
   display: flex;
   flex-direction: column;
   align-items: left;
}
.info,
.help,
.company {
   padding-right: 3vw;
}
.company div div,
.info div div,
.help div div {
   font-size: 1.1vw;
   cursor: pointer;
   margin-bottom: 0.5vw;
}
.company div div:hover,
.info div div:hover,
.help div div:hover {
   text-decoration: underline;
}
h6 {
   font-size: 1.2vw;
   font-weight: 600;
   margin-bottom: 1vw;
}
.socials {
   border: none;
}
.socials div {
   text-align: left;
}
.socials div div {
   display: flex;
   justify-content: left;
   gap: 1vw;
}
.socials img {
   width: 2.5vw;
   opacity: 0.7;
   cursor: pointer;
   transition: opacity 0.1s;
}
.socials img:hover {
   opacity: 0.6;
}
.bottom {
   display: flex;
   justify-content: space-between;
}
.bottom div {
   font-size: 1.1vw;
   color: rgba(0, 0, 0, 0.59);
}
button {
   background: none;
   border: none;
   display: flex;
   align-items: center;
   gap: 0.5vw;
   cursor: pointer;
}
button span {
   font-size: 1.3vw;
   font-weight: 500;
}
button img {
   width: 1.6vw;
   opacity: 0.65;
   transform: rotate(180deg);
}
@media (width < 550px) {
   footer {
      padding: 5vw;
   }
   .top {
      flex-wrap: wrap;
      gap: 6vw 2.3vw;
   }
   .company div div,
   .info div div,
   .help div div {
      font-size: 3vw;
      margin-bottom: 1vw;
   }
   .company, .info {
      padding-right: 6vw;
   }
   .socials {
      border: none;
      flex: 1;
   }
   .help {
      border: none;
      padding-right: 0;
   }
   h6 {
      font-size: 3.5vw;
   }
   .socials div{
      align-self: center;
      text-align: center;
   }
   .socials div div{
      gap: 3vw;
   }
   .socials h6 {
      margin-bottom: 3vw;
   }
   .socials img {
      width: 6vw;
   }
   .bottom div {
      font-size: 2.2vw;
   }
   button span {
      font-size: 2.8vw;
   }
   button img {
      width: 2.7vw;
   }
}
</style>
