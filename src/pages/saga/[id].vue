<script setup lang="ts">
import { useRoute } from 'vue-router/auto';
import { supabase } from '@/supabase';
import AfficheSaga from '@/components/AfficheSaga.vue';

const route = useRoute('/saga/[id]');

let {data : film, error} = await supabase
    .from('Films')
    .select(`
    *,
    Celebrite(*),
    Genre(*),
    Saga(*),
    Support(*),
    Plateforme(*),
    Variante(*)
    `)
    .eq('id', route.params.id)
    .single();

console.log("data film",film);
</script>

<template>
    <div>
        <AfficheSaga v-bind="film" />
    </div>
</template>