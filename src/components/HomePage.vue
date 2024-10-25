<template>
  <div>
    <h2>Welcome to the Home Page!</h2>
    <div v-if="user">
    <h1>Bienvenue, {{ user.name }} !</h1>
  </div>
  Cliquer pour ralentir ({{ clicks }} secondes d'attente) !

    <!-- Button with increasing wait time -->
    <AsyncButton :color="'primary'" :delay="clicks" @click="increaseClicks">
      
    </AsyncButton>
    
  </div>
</template>

<script>

import AsyncButton from './AsyncButyon.vue';
import { signInAndGetUser } from '../lib/microsoftGraph';

export default {
  name: 'HomePage', 

  props: {
    user: {
      type: Object,
      default: null
    }
  },
  components: {
     AsyncButton
  },
  data() {
    return {
      clicks: 1 // Initialise le compteur à 1
    };
  },
  
  methods: {
   
    increaseClicks() {
      this.clicks += 1; // Incrémente le compteur à chaque clic
    },
    async signInWithMicrosoft() {
      
      const user = await signInAndGetUser();
      this.$emit('user-signed-in', user);
    }
  }
}
</script>

<style scoped>
/* Add additional styles for HomePage if needed */
</style>