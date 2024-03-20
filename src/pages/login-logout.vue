<script setup lang="ts">
  import { supabase, user } from '../supabase';
</script>

<template>
  <div class="flex items-center">
    <button v-if="user" @pointerdown="supabase.auth.signOut()" class="bg-red-500 hover:bg-red-600 text-white font-semibold py-2 px-4 rounded-md transition duration-300 ease-in-out">
      Se déconnecter ({{ user.email }})
    </button>
    <button v-else @pointerdown="signInWithFigma()" class="bg-gray-800 hover:bg-gray-900 text-white font-semibold py-2 px-4 rounded-md transition duration-300 ease-in-out">
      Se connecter avec Figma
    </button>
  </div>
</template>

<script setup lang="ts">
  import { useRouter } from 'vue-router';

  const router = useRouter();

  const signInWithFigma = async () => {
    try {
      const { user, error } = await supabase.auth.signInWithOAuth({ provider: 'figma' });

      if (error) {
        throw error;
      }

      console.log('Signed in successfully with Figma', user);
      // Rediriger l'utilisateur vers une page après la connexion
      router.push('/');
    } catch (error) {
      console.error('Error signing in with Figma:', error.message);
    }
  };
</script>
