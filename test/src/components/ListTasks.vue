<template>
  <div class="list-tasks">
    <ContainerTasks 
      title="Счетчик количества продуктов"
    >
      <CountProducts />
    </ContainerTasks>
    <ContainerTasks 
      title="Поиск по списку имен"
    >
      <SearchFromArray />
    </ContainerTasks>
    <ContainerTasks 
      title="Простая пагинация"
    >
      <Pagination />
    </ContainerTasks>
    <ContainerTasks 
      title="Вывод списка карточек товаров с добавлением в корзину"
    >
      <ListProducts />
    </ContainerTasks>
  </div>
</template>

<script>
import ContainerTasks from './general/ContainerTask.vue';
import CountProducts from '@/components/CountProducts.vue';
import SearchFromArray from '@/components/SearchFromArray.vue';
import Pagination from '@/components/Pagination.vue';
import ListProducts from '@/components/ListProducts.vue';

export default {
  name: "ListTasks",
  components: {
    ContainerTasks,
    CountProducts,
    SearchFromArray,
    Pagination,
    ListProducts,

  },
  setup() {
    return {

    };
  },
};
</script>

<styles scoped lang="scss">
  @import "./styles/ListTasks/component";
</styles>
