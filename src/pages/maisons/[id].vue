<script setup lang="ts">
import { useRoute } from 'vue-router/auto';
import { defineProps } from 'vue';
import type { SchemaFilms } from '@/types';
import { supabase } from '@/supabase';
const route = useRoute('/maisons/[id]');
// charge le film depuis supabase
let {data : film, error} = await supabase
    .from('Films')
    .select('*')
    .eq('id', route.params.id)
    .single();
</script>

<template>
    <div>
        test affiche id : {{ route.params.id }}
        <h2>{{ titre_film }}</h2>
        <p>{{ description_film }}</p>
    </div>
</template>