<script setup lang="ts">
import { supabase, user } from '../supabase';
</script>
<template>
<div class="pt-72">
    <button v-if="user" @pointerdown="supabase.auth.signOut()">
        Se déconnecter 
    </button>
    <button v-else @pointerdown="supabase.auth.signInWithOAuth({provider: 'github'})">
        Se connecter avec Github
    </button>
</div>
</template>