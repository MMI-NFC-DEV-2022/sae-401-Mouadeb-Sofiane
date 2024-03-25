<script setup lang="ts">
import type { SchemaFilms } from '@/types';
import { supabase } from '@/supabase';
import AfficheCelebrite from '@/components/AfficheCelebrite.vue';
 
console.log(supabase);
    
let {data : tableaucelebrite, error} = await supabase
    .from('Celebrite')
    .select('*');
</script>

<template>
    <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-2 gap-6-4 bg-pink-100">
        <AfficheCelebrite v-for="celebrite in tableaucelebrite" v-bind="celebrite" />
    </div>
</template>