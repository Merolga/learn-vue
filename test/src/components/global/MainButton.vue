<template>
    <button
        type="button"
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
}
</script>

<styles scoped lang="scss">
  @import './styles/MainButton/component';
</styles>