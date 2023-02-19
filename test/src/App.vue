<template>
  <div class="app">
    <ListTasks />
  </div>
</template>

<script>
import ListTasks from './components/ListTasks.vue';

export default {
  name: 'App',
  components: {
    ListTasks,
  }
}
</script>

<styles scoped lang="scss">
  @import "./styles/component";
</styles>
  
