<template>
    <button
        type="button"
        :class="{'main-button--is-active': active}"
        class="main-button"
      >
        <span class="main-button__label">
          <slot></slot>
        </span>
    </button>
</template>

<script>


export default {
  name: 'MainButton',
  props: {
    active: {
      type: Boolean,
      default: false,
    }
  },
}
</script>

<styles scoped lang="scss">
  @import './styles/MainButton/component';
</styles>