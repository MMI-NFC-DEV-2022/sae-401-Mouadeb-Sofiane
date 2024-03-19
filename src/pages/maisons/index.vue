<script setup lang="ts">
import type { SchemaFilms } from '@/types';
import { supabase } from '@/supabase';
import AfficheFilm from '@/components/AfficheFilm.vue';
 
console.log(supabase);
    
let {data : tableaufilms, error} = await supabase
    .from('Films')
    .select('*');
</script>

<template>
    <div class="grid grid-cols-3 gap-4">
        <AfficheFilm v-for="films in tableaufilms" v-bind="films" />
    </div>
</template>