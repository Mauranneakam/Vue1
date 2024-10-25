<template>
  <div>
    <h2>Welcome to the Home Page!</h2>
    <BaseButton color="primary" :isDisabled="false">Primary Button</BaseButton>
    <BaseButton color="warn" :isDisabled="false">Warn Button</BaseButton>
    <BaseButton color="danger" :isDisabled="false">Danger Button</BaseButton>
    
    
    <!-- Button with increasing wait time -->
    <AsyncButton :color="'primary'" :delay="clicks" @click="increaseClicks">
      Cliquer pour ralentir ({{ clicks }} secondes d'attente) !
    </AsyncButton>
    <BaseButton color="primary" @click="signInWithMicrosoft">Sign In with Microsoft</BaseButton>
  </div>
</template>

<script>
import BaseButton from './BaseButton.vue';
import AsyncButton from './AsyncButyon.vue';
import { signInAndGetUser } from '../lib/microsoftGraph';

export default {
  name: 'HomePage', 

  components: {
    BaseButton, AsyncButton
  },
  data() {
    return {
      clicks: 1 // Initialise le compteur à 1
    };
  },
  
  methods: {
   
    async signInWithMicrosoft() {
      const user = await signInAndGetUser(); // Appelle la fonction signInAndGetUser
      if (user) {
        alert(`Connexion réussie ! Bienvenue, ${user.name}`);
      } else {
        alert('Échec de la connexion');
      }
    }
  }
}
</script>

<style scoped>
/* Add additional styles for HomePage if needed */
</style>