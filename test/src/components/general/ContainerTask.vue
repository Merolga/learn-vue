<template>
  <section class="container-task">
    <button 
      @click="showContent()"
      class="container-task__btn container-task-btn"
    >
      <span class="container-task-btn__label">{{ title }}</span>
      <img 
        src="../../assets/arrow-down.svg"
        alt="Arrow"
        :class="{'container-task-btn__icon--rotate': isVisibleContent}"
        class="container-task-btn__icon"
      >
    </button>  
    <div 
      v-show="isVisibleContent"
      class="container-task__content"
    >
      <slot></slot>
    </div>
  </section>
</template>

<script>
import {ref, unref} from "vue";

export default {
  name: 'ContainerTask',
  props: {
    title: {
      type: String,
      default: 'Какая-то задача',
    },
  },
  setup() {
    const isVisibleContent = ref(false);  
    
    const showContent = () => isVisibleContent.value = !unref(isVisibleContent);
    
    return {
      isVisibleContent,
      showContent,
    }
  },
}
</script>

<styles scoped lang="scss">
  @import './styles/ContainerTask/component';
</styles>