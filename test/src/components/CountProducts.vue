<template>
  <div class="count-products">
    <p class="count-products__label count-products__label--size-m">Выберите кол-во продуктов:</p>
    <div class="count-products__row">
      <MainButton @click="substractProduct()" class="count-products__btn"> - </MainButton>
      <input type="number" v-model="countProducts" readonly="readonly" />
      <MainButton @click="addProduct()" class="count-products__btn"> + </MainButton>
    </div>
    <p class="count-products__label count-products__label--size-s">Количество можно указать в диапазоне от 1 до 10</p>
  </div>
</template>

<script>
import { ref, unref } from "vue";
import MainButton from "./general/MainButton.vue";

export default {
  name: "CountProducts",
  components: {
    MainButton,
  },
  setup() {
    let countProducts = ref(1);

    const addProduct = () =>
      unref(countProducts) < 10 ? countProducts.value++ : 10;
    const substractProduct = () =>
      unref(countProducts) > 1 ? --countProducts.value : 1;

    return {
      countProducts,
      addProduct,
      substractProduct,
    };
  },
};
</script>

<styles scoped lang="scss">
@import "./styles/CountProducts/component";
</styles>
