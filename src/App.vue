<template>
  <div id="app">
    <BaseLayout>
      <template #main>
        <HomePage/>
      </template>
    </BaseLayout>
  </div>
</template>

<script>
import HomePage from './components/HomePage.vue';
import BaseLayout from './components/BaseLayout.vue';

export default {
  name: 'App',
  components: {
    BaseLayout,
    HomePage
  },
  data() {
    return {
      user: null // Store the user information here
    };
  },
  
}
</script>

<style scoped>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  color: #000203;
  margin-top: 60px;
}

main {
  padding: 20px;
  margin-bottom: 60px; /* To avoid overlap with the footer */
}
</style>