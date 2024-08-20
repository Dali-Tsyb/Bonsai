<script setup>
import ItemList from "./ItemList.vue";

defineProps({
   selectOption: Function,
   showDropdown: Boolean,
   toggleDropdown: Function,
   selectedOption: Object,
   options: Array,
   nextPage: Function,
   prevPage: Function,
   isFirstPage: Boolean,
   isLastPage: Boolean,
});

const placeholder = "СОРТИРОВАТЬ";

</script>

<template>
   <div class="catalogue">
      <div class="catalogue-header">
         <div class="catalogue-title">КАТАЛОГ</div>
         <div class="dropdown">
            <button class="dropdown-button" @click="toggleDropdown">
               <span>{{
                  selectedOption.text ? selectedOption.text : placeholder
               }}</span>
               <img src="/icons/arrow.png" alt="arrow down" class="arrow" />
            </button>
            <ul class="dropdown-list" v-if="showDropdown">
               <li
                  v-for="(option, index) in options"
                  :key="index"
                  @click="selectOption(option)"
               >
                  {{ option.text }}
               </li>
            </ul>
         </div>
      </div>
      <ItemList />
      <div class="catalogue-pagination">
         <img
            @click="prevPage"
            src="/icons/arrow.png"
            alt=""
            :class="['prev-page', isFirstPage ? 'disabled' : '']"
         />
         <img
            @click="nextPage"
            src="/icons/arrow.png"
            alt=""
            :class="['next-page', isLastPage ? 'disabled' : '']"
         />
      </div>
   </div>
</template>

<style scoped>
.catalogue {
   margin: 2vw 3vw;
   padding: 4vw;
   background: rgba(255, 255, 255, 0.787);
   backdrop-filter: blur(8px);
   border-radius: 40px;
   box-shadow: 0 0 13px rgba(255, 255, 255, 0.461);
}
.catalogue-header {
   display: flex;
   width: 100%;
   justify-content: start;
   align-items: center;
   gap: 2vw;
}
.catalogue-title {
   font-size: 2.3vw;
   font-weight: 600;
   color: rgb(74, 74, 74);
}
.dropdown {
   position: relative;
   z-index: 20;
   border-left: 1px solid rgba(0, 0, 0, 0.327);
   width: max-content;
}
.dropdown-button {
   background-color: #ffffff00;
   border: none;
   padding: 1vw 2vw;
   cursor: pointer;
   display: flex;
   align-items: center;
   gap: 2vw;
}
.dropdown-button span {
   font-size: 1.2vw;
   font-weight: 500;
   color: rgba(0, 0, 0, 0.65);
}
.arrow {
   width: 1.3vw;
   opacity: 60%;
}
.dropdown-list {
   position: absolute;
   top: 100%;
   left: 0;
   background: linear-gradient(rgba(255, 255, 255, 0), rgb(220, 220, 220) 50%);
   width: max-content;
}

.dropdown-list li {
   font-size: 1vw;
   font-weight: 500;
   color: rgba(0, 0, 0, 0.575);
   padding: 1vw 2vw;
   cursor: pointer;
   transition: background 0.2s;
}

.dropdown-list li:hover {
   background: rgba(255, 255, 255, 0.397);
}
.catalogue-pagination {
   z-index: 0;
   display: flex;
   justify-content: center;
   align-items: center;
   gap: 2vw;
   margin-top: 3vw;
}
.prev-page,
.next-page {
   width: 2vw;
   opacity: 65%;
   cursor: pointer;
}
.prev-page {
   transform: rotate(90deg);
}
.next-page {
   transform: rotate(-90deg);
}
.next-page.disabled,
.prev-page.disabled {
   opacity: 0.4;
   pointer-events: none;
}
@media (width < 800px) {
   .catalogue-title {
      font-size: 2.5vw;
   }
   .catalogue-filters li,
   .sorting {
      font-size: 1.5vw;
   }
   .dropdown-list li {
      font-size: 1.3vw;
   }
}
@media (width < 550px) {
   .catalogue {
      padding: 6vw;
   }
   .catalogue-title {
      font-size: 3vw;
   }
   .catalogue-filters li,
   .sorting {
      font-size: 2vw;
   }
   .dropdown-button span {
      font-size: 3vw;
   }
   .dropdown-list li {
      font-size: 2.7vw;
      padding: 2vw;
   }
   .arrow {
      width: 4vw;
   }
   .prev-page, .next-page {
      width: 6vw;
   }
   .catalogue-pagination {
      margin-top: 12vw;
   }
}
@media (width < 400px) {
   .catalogue {
      padding: 8vw;
   }
   .catalogue-title {
      font-size: 5.5vw;
   }
   .catalogue-filters li,
   .sorting {
      font-size: 3.5vw;
   }
}
</style>
