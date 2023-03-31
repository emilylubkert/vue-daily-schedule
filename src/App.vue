<script setup>
import Date from './components/Date.vue';
import Goal from './components/Goal.vue';
import Schedule from './components/Schedule.vue';
import ToDoList from './components/ToDoList.vue';

</script>

<template>
  <div id="app">
    <Date />
    <Goal />
    <ToDoList />
    <Schedule />
  </div>

</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
