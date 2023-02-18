<template>
  <div class="lo">
    <h2>Счетчик количества продуктов</h2>
    <p>Выберите кол-во продуктов:</p>
    <div class="lo__row">
      <MainButton @click="substractProduct()" class="lo__btn"> - </MainButton>
      <input type="number" v-model="countProducts" readonly="readonly" />
      <MainButton @click="addProduct()" class="lo__btn"> + </MainButton>
    </div>
  </div>
</template>

<script>
import { ref } from "vue";
import MainButton from "./global/MainButton.vue";

export default {
  name: "LessonOne",
  components: {
    MainButton,
  },
  setup() {
    let countProducts = ref(1);

    const addProduct = () =>
      countProducts.value < 10 ? countProducts.value++ : 10;
    const substractProduct = () =>
      countProducts.value > 1 ? --countProducts.value : 1;

    return {
      countProducts,
      addProduct,
      substractProduct,
    };
  },
};
</script>

<styles scoped lang="scss">
@import "./styles/LessonOne/component";
</styles>
