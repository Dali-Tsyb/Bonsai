<template>
   <div class="about">
      <div class="about-company">
         <h6>О компании:</h6>
         Наш клуб был создан в 2007 году группой энтузиастов, увлеченных этим
         искусством, которые хотели улучшить организацию деятельности в этой
         области и сделать доступным всё разнообразие бонсай. Сегодня нам уже 15
         лет, мы собираем самые интересные экземпляры, сотрудничая с мастерскими
         из разных стран мира, успели не один раз появиться на телевидении,
         проводим тематические мероприятия и, конечно же, представляем собственную
         торговую площадку, где представители любой школы бонсай могут выставить
         на продажу свои работы.
         <div class="about-company-button">Узнать больше</div>
      </div>
      <div class="about-stores">
         <h6>Где нас можно найти:</h6>
         <ul>
            <li>
               <img src="/icons/location.png" alt="location" />
               <div class="address">
                  Москва, Серпуховский вал 17к1. (вход в арку у дикси)
               </div>
               <div class="phone">Телефон: (495) 921-10-25</div>
            </li>
            <li>
               <img src="/icons/location.png" alt="location" />
               <div class="address">
                  Санкт-Петербург, Черняховского 34. (вход со двора)
               </div>
               <div class="phone">Телефон: (812) 777-28-75</div>
            </li>
         </ul>
      </div>
      <div class="about-specials">
         <h6>Только у нас:</h6>
         <ul>
            <li>
               Все бонсаи пострижены нашими мастерами и являются произведением
               искусства
            </li>
            <li>
               Уникальная клубная система. Всегда бесплатно: стрижка вашего
               дерева, снабжение удобрениями, уход во время вашего отпуска,
               консультации, скидки
            </li>
            <li>
               Все деревья в великолепных керамических плошках и хорошем грунте
            </li>
            <li>
               Набор подарков с каждым деревом: подарочный пакет, удобрение,
               статуэтка под бонсай, клубная карта, описание значения дерева и
               инструкция по содержанию
            </li>
         </ul>
      </div>
   </div>
</template>

<style scoped>
.about {
   margin: 2vw 3vw;
   padding: 7vw 4vw;
   background: rgba(255, 255, 255, 0.787);
   backdrop-filter: blur(8px);
   border-radius: 40px;
   box-shadow: 0 0 13px rgba(255, 255, 255, 0.461);
}
h6 {
   font-size: 1.8vw;
   font-weight: 500;
   margin-bottom: 2vw;
}
.about-company {
   font-size: 1.4vw;
   color: rgb(74, 74, 74);
   border-bottom: 1px solid rgba(0, 0, 0, 0.112);
   padding: 0 3vw 3vw 3vw;
   line-height: 1.6vw;
}
.about-company-button {
   text-transform: uppercase;
   font-size: 1vw;
   letter-spacing: 0.06vw;
   color: rgb(245, 245, 245);
   background: rgb(112, 138, 112);
   border-radius: 100px;
   box-shadow: 0 0 15px rgba(105, 105, 105, 0.374);
   width: fit-content;
   margin-top: 3vw;
   padding: 1vw 2vw;
   cursor: pointer;
   transition: background 0.2s;
}
.about-company-button:hover {
   background: rgb(140, 169, 140);
}
.about-company-button:active {
   background: rgb(112, 138, 112);
}
.about-stores {
   padding: 3vw;
   border-bottom: 1px solid rgba(0, 0, 0, 0.112);
}
.about-stores ul {
   display: flex;
   flex-direction: column;
   gap: 1.5vw;
}
.about-stores li {
   display: grid;
   grid-template-areas:
      "img address"
      "img phone";
   grid-template-columns: 3vw 1fr;
   align-items: center;
   gap: 0.5vw 1vw;
}
.about-stores li img {
   grid-area: img;
   width: 100%;
   filter: invert(1);
   opacity: 0.5;
}
.address {
   grid-area: address;
   font-size: 1.3vw;
   color: rgb(74, 74, 74);
}
.phone {
   grid-area: phone;
   font-size: 1.3vw;
   color: rgb(74, 74, 74);
}
.about-specials {
   padding: 3vw 3vw 0 3vw;
}
.about-specials li {
   list-style: disc;
   font-size: 1.3vw;
   color: rgb(74, 74, 74);
   margin: 0 0 1vw 1.5vw;
}
@media (width < 550px) {
   .about {
      padding: 12vw 8vw;
   }
   h6 {
      font-size: 6vw;
      margin-bottom: 7vw;
   }
   .about-company {
      font-size: 4vw;
      line-height: 4.5vw;
      padding: 0 3vw;
   }
   .about-company-button {
      font-size: 3vw;
      padding: 3vw 5vw;
      margin: 6vw 0;
   }
   .about-stores {
      padding: 6vw 3vw;
   }
   .about-stores ul {
      gap: 6vw;
   }
   .address, .phone {
      font-size: 3.5vw;
   }
   .about-stores li {
      gap: 0 9vw;
   }
   .about-stores li img {
      width: 9vw;
   }
   .about-specials {
      padding: 6vw 3vw;
   }
   .about-specials li {
      font-size: 4vw;
      margin: 0 0 2vw 5.6vw;
   }
}
</style>
