<script setup lang="ts">
import { useRoute } from 'vue-router/auto';
import { defineProps } from 'vue';
import { supabase } from '@/supabase';
const route = useRoute('/saga/[id]');
import type { Database, Tables } from '@/supabase-types';
defineProps <Database["public"]["Tables"]["Films"]["Row"] & {Celebrite:Tables<'Celebrite'>[]} & {Genre:Tables<'Genre'>[]} & {Saga:Tables<'Saga'>[]} & {Variante:Tables<'Variante'>} & {Support:Tables<'Support'>} & {Plateforme:Tables<'Plateforme'>}>()
</script>

<template>
     <div class="p-5 mb-24">
        <div v-for="uneSaga in Saga">
            <h1 class="text-center text-6xl mb-16 mt-16">{{ uneSaga.nom_de_la_saga }}</h1>
            <div class="flex gap-4">
                <img :src="uneSaga.image_saga" class="w-40 h-44">
            
                <div class="flex flex-col">
                    <div class="flex pb-2">
                        <p class="text-l underline">Synopsis de la saga</p>
                        <p class="ml-5 text-justify">{{ uneSaga.description_saga }}</p>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>