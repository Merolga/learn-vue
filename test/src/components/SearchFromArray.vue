<template>
  <div class="search-from-array">
    <input 
      v-model="foundWord"
      type="text"
    >
    <p class="search-from-array__label">{{ `Всего имен: ${listNames.length}, найдено совпадений: ${filteredNames.length}` }}</p>
    <ul>
      <li
        v-for="(name, index) in filteredNames"
        :key="`search-from-array-item-${index}`"
        class="search-from-array__item"
      >
        {{ name }}
      </li>
    </ul>
  </div>
</template>

<script>
import { ref, unref, computed } from "vue";
import {listNames} from '@/constants/constants.ts';

export default {
  name: "SearchFromArray",
  components: {

  },
  setup() {
    const foundWord = ref('');
    const filteredNames = computed(() => {
      return listNames.filter(item => item.toLowerCase().includes((unref(foundWord)).toLowerCase()));
    });

    return {
      listNames,
      filteredNames,
      foundWord,
    };
  },
};
</script>

<styles scoped lang="scss">
  @import "./styles/SearchFromArray/component";
</styles>
