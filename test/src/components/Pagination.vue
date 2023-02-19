<template>
  <div class="pagination">
    <ul class="pagination__list">
      <li 
        v-for="(name, index) in getSublist[currentPage - 1]"
        :key="`pagination-item-${index}`"
      >
        {{ name }}
      </li>
    </ul>
    <div class="pagination__btns">
      <MainButton 
        @click="getPreviousPage()"
        :disabled="currentPage == 1"
      >
        пред.
      </MainButton>
      <MainButton 
        v-for="page in pages"
        @click="currentPage = page"
        :key="`pagination-button-${page}`"
        :active="currentPage == page"
      >
        {{ page }}
      </MainButton>
      <MainButton 
        @click="getNextPage()"
        :disabled="currentPage == pages"
      >
        след.
      </MainButton>
    </div>
    <p class="pagination__label">{{ `Страница ${currentPage} из ${pages}` }}</p>
  </div>
</template>

<script>
import { ref, computed } from "vue";
import {listNamesLarge} from '@/constants/constants.ts';
import MainButton from "./general/MainButton.vue";

export default {
  name: "CountProducts",
  components: {
    MainButton,
  },
  setup() {
    const countElements = ref(5);
    let currentPage = ref(1);

    const getPreviousPage = () => currentPage.value > 1 ? currentPage.value-- : currentPage.value;
    const getNextPage = () => currentPage.value < (getSublist.value).length ? currentPage.value++ : currentPage.value;
    const getSublist = computed(() => {
      let arr = [];
      const result = [];
      for (let i = 0; i < listNamesLarge.length; i++) {
        arr.push(listNamesLarge[i])
        if (((i + 1) % countElements.value == 0)) {
          result.push(arr);
          arr = [];
        }
      }
      result.push(arr);

      return result;
    });

    const pages = computed(() => (getSublist.value).length)

    return {
      pages,
      currentPage,
      getPreviousPage,
      getNextPage,
      listNamesLarge, 
      getSublist,
    };
  },
};
</script>

<styles scoped lang="scss">
@import "./styles/Pagination/component";
</styles>
