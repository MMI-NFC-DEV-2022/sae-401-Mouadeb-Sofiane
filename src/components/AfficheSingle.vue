<script setup lang="ts">
import { useRoute } from 'vue-router/auto';
import { defineProps } from 'vue';
import type { SchemaFilms } from '@/types';
import { supabase } from '@/supabase';
const route = useRoute('/maisons/[id]');
defineProps<SchemaFilms>()
let {data : film, error} = await supabase
    .from('Films')
    .select('*')
    .eq('id', route.params.id)
    .single();
</script>

<template>
    <div>
        <h2>{{ titre_film }}</h2>
        <p>{{ description_film }}</p>
    </div>
</template>