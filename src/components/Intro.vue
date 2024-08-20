<script setup></script>

<template>
   <div class="container">
      <div class="blur" ref="blur"></div>
      <div class="intro" ref="intro">
         <div class="intro-text-title">
            <div class="intro-text-title-brand">БОНСАЙ.РФ</div>
            <div class="intro-text-title-slogan">Живые растения с историей</div>
         </div>
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
                  Бесплатно: стрижка Вашего дерева, снабжение удобрениями,
                  гостиница для бонсай
               </p>
            </li>
         </ul>
         <img class="intro-tree" src="/img/tree.png" alt="bonsai tree" />
      </div>
   </div>
</template>

<style scoped>
.container {
   width: 100%;
   height: 100%;
   display: flex;
   justify-content: center;
   align-items: center;
   padding: 2vw 3vw;
   margin-top: 3vw;
}
.intro {
   position: relative;
   height: 100%;
   padding-left: 6%;
   background: rgba(255, 255, 255, 0.787);
   backdrop-filter: blur(8px);
   border-radius: 40px;
   box-shadow: 0 0 13px rgba(255, 255, 255, 0.461);
   display: grid;
   grid-template-columns: 55% 45%;
   grid-template-areas:
      "title tree"
      "specials tree";
   justify-content: start;
   overflow: hidden;
   width: 100%;
}
.intro-text-title {
   grid-area: title;
   margin-top: 4vw;
}
.intro-text-title-brand {
   font-family: "Yeseva One";
   font-size: 8vw;
}
.intro-text-title-slogan {
   grid-area: title;
   font-weight: 400;
   font-size: calc(16px + 0.4vw);
}
.intro-text-specials {
   grid-area: specials;
   display: flex;
   width: 100%;
   align-items: baseline;
   justify-content: space-between;
   gap: 2vw;
   text-align: center;
   flex-wrap: wrap;
}
li {
   flex: 1 1 0;
   opacity: 0.7;
}
.gift,
.delivery,
.card {
   opacity: 70%;
}
.gift,
.delivery {
   filter: invert(1);
}
.gift {
   width: 3vw;
   margin-bottom: 1vw;
}
.delivery {
   width: 4vw;
   margin-bottom: 1vw;
}
.card {
   width: 4vw;
   margin-bottom: 1vw;
}
h6 {
   font-size: calc(10px + 0.25vw);
   font-weight: 600;
   text-transform: uppercase;
   margin-bottom: 4%;
}
p {
   font-size: calc(10px + 0.25vw);
}
.intro-tree {
   position: absolute;
   grid-area: tree;
   transform: translateY(1%);
   width: 100%;
   height: 100%;
   object-fit: cover;
   overflow: visible;
}

@media (width > 2000px) {
   h6 {
      font-size: calc(10px + 0.3vw);
   }
   p {
      font-size: calc(10px + 0.3vw);
   }
}
@media (width < 830px) {
   .intro {
      grid-template-columns: 50% 50%;
   }
   .intro-text-specials {
      flex-direction: column;
      text-align: left;
      align-items: center;
      margin: 6vw 1vw;
   }
   .intro-text-specials * {
      margin: 0;
   }
   li {
      display: grid;
      grid-template-areas:
         "icon title"
         "icon text";
      grid-template-columns: 15% 75%;
      align-items: center;
      gap: 1vw;
      flex: 0 0 0;
   }
   .gift,
   .delivery,
   .card {
      grid-area: icon;
      width: 80%;
   }
   h6 {
      grid-area: title;
   }
   p {
      grid-area: text;
   }
   .intro-tree {
      transform: translateY(4%);
   }
}
@media (width < 550px) {
   .container {
      padding: 4vw 3vw;
      margin-top: 10vw;
   }
   .intro {
      grid-template-areas:
         "title"
         "slogan"
         "tree";
      grid-template-columns: 100%;
      grid-auto-rows: auto;
      padding: 12vw 1vw 0 1vw;
      text-align: center;
      gap: 4vw;
   }
   .intro-text-specials {
      display: none;
   }
   .intro-text-title-brand {
      font-size: 10vw;
   }
   .intro-text-title-slogan {
      font-size: 3.5vw;
   }
   .intro-tree {
      transform: rotate(6deg) translateX(-2%) translateY(-40%);
   }
}
</style>
