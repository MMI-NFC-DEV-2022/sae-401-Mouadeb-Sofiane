<script setup lang="ts">
import { useRoute } from 'vue-router/auto';
import { defineProps } from 'vue';
import { supabase } from '@/supabase';
const route = useRoute('/saga/[id]');
import type { Database, Tables } from '@/supabase-types';
defineProps <Database["public"]["Tables"]["Saga"]["Row"] & {Films:Tables<'Films'>[]} & {Genre:Tables<'Genre'>[]} & {Saga:Tables<'Saga'>[]} & {Variante:Tables<'Variante'>} & {Support:Tables<'Support'>} & {Plateforme:Tables<'Plateforme'>}>()
</script>

<template>
     <div class="p-5 mb-24">
        <div >
            <h1 class="text-center text-6xl mb-16 mt-16">{{ nom_de_la_saga }}</h1>
            <div class="flex gap-4">
                <img :src="image_saga" class="w-40 h-44 object-cover">
            
                <div class="flex flex-col">
                    <div class="flex pb-2">
                        <p class="text-l underline">Synopsis de la saga</p>   
                    </div>
                    <p class="ml-5 mr-5 text-justify">{{ description_saga }}</p>
                </div>
                
            </div>
        </div>
        <div>
            <p class="text-center mt-5 mb-5 text-3xl">Les films issus de la saga</p>
            <div class="flex gap-5 m-auto">
                    <img v-for="unFilm in Films" class="rounded-md m-auto w-40" :src="unFilm.image_film" >
            </div>
        </div>
    </div>
    
</template>