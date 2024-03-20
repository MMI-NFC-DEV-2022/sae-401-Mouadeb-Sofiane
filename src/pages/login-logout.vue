<script setup lang="ts">
  import { supabase, user } from '../supabase';
  import { ref } from 'vue';

  const email = ref('');
  const password = ref('');
  const error = ref(null);

  const signInWithEmail = async () => {
    try {
      const { user, error } = await supabase.auth.signIn({
        email: email.value,
        password: password.value
      });

      if (error) {
        throw error;
      }

      console.log('Signed in successfully', user);
    } catch (error) {
      console.error('Error signing in:', error.message);
      error.value = error.message;
    }
  };
</script>

<template>
  <div class="flex items-center">
    <button v-if="user" @pointerdown="supabase.auth.signOut()" class="bg-red-500 hover:bg-red-600 text-white font-semibold py-2 px-4 rounded-md transition duration-300 ease-in-out">
      Se déconnecter ({{ user.email }})
    </button>
    <div v-else>
      <input v-model="email" type="email" placeholder="E-mail" class="border border-gray-300 rounded-md px-2 py-1 mr-2">
      <input v-model="password" type="password" placeholder="Mot de passe" class="border border-gray-300 rounded-md px-2 py-1 mr-2">
      <button @click="signInWithEmail" class="bg-blue-500 hover:bg-blue-600 text-white font-semibold py-2 px-4 rounded-md transition duration-300 ease-in-out">
        Se connecter avec E-mail et Mot de passe
      </button>
      <p v-if="error" class="text-red-500">{{ error }}</p>
    </div>
  </div>
</template>
