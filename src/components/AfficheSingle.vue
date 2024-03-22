<script setup lang="ts">
import { useRoute } from 'vue-router/auto';
import { defineProps } from 'vue';
import { supabase } from '@/supabase';
const route = useRoute('/films/[id]');
import type { Database, Tables } from '@/supabase-types';
defineProps <Database["public"]["Tables"]["Films"]["Row"] & {Celebrite:Tables<'Celebrite'>[]} & {Genre:Tables<'Genre'>[]} & {Saga:Tables<'Saga'>[]} & {Variante:Tables<'Variante'>} & {Support:Tables<'Support'>} & {Plateforme:Tables<'Plateforme'>}>()
</script>

<template>
    <div>
        <div class="flex gap-14">
            <p class="text-xl">{{ date_film }}</p> | 
            <p class="text-xl">{{ temps_film }}</p>
            <div class="flex pl-2 pb-2">
            <div v-for="n in note_film??0" class="text-gray-200">
                <svg class="w-5 h-5 fill-current text-yellow-500" viewBox="0 0 24 24">
                    <path d="M12 2L14.47 8.53L21 9.35L16.24 13.77L17.47 20.07L12 17.77L6.53 20.07L7.76 13.77L3 9.35L9.53 8.53L12 2Z" />
                </svg>
            </div>
            <div v-for="n in (5-(note_film??0))" class="text-gray-200 ">
                <svg class="w-5 h-5 fill-current text-gray-300" viewBox="0 0 24 24">
                    <path d="M12 2L14.47 8.53L21 9.35L16.24 13.77L17.47 20.07L12 17.77L6.53 20.07L7.76 13.77L3 9.35L9.53 8.53L12 2Z" />
                </svg>
            </div>
        </div>
        </div>
        
        <h2>{{ titre_film }}</h2>
        <img :src="image_film" />
        <div>
            <h2>Synopsis :</h2>
                <p>{{ description_film }}</p>
            <h2>Acteurs :</h2>
                <div class="flex gap-1">
                    <p v-for="uneCelbrite in Celebrite">{{ uneCelbrite.prenom_celebrite }}</p>
                    <p v-for="uneCelbrite in Celebrite">{{ uneCelbrite.nom_celebrite }}</p>
                </div>
        </div>
            <RouterLink :to="`/celebrite/${id}`">
                <div v-for="uneCelbrite in Celebrite">
                    <img :src="uneCelbrite.photo_celebrite" alt="Photo Acteurs">
                </div>
            </RouterLink>

    <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-2 gap-6">
        <div v-for="unSupport in Support" class="ml-10">
        <h2>Où acheter</h2>
            <div class="ml-10">
                <p>{{ unSupport.support_type }}</p>
                    <img :src="unSupport.support_img">
                <p>Acheter à {{ unSupport.support_prix }}</p>
                <RouterLink :to="`/support/${id}`">
                    <button class="rounded-full bg-blue-300 p-2">
                        + d'infos
                    </button>
                </RouterLink>
            </div>
        </div>
        <div v-for="unePlateforme in Plateforme" class="ml-10">
        <h2>Où louer</h2>
            <div class="ml-10">
                <p>{{ unePlateforme.plateforme_streaming }}</p>
                    <img :src="unePlateforme.logo">
                <p >Louer à partir de {{ unePlateforme.plateforme_prix }}</p>
                <RouterLink :to="`/plateforme/${id}`">
                    <button class="rounded-full bg-blue-300 p-2 text-center">
                        + d'infos
                    </button>
                </RouterLink>
            </div>
        </div>
    </div>




        
        <p v-for="unGenre in Genre">{{ unGenre.genre_film }}</p>
        <RouterLink :to="`/celebrite/${id}`">Celebrite</RouterLink>
        <RouterLink :to="`/genre/${id}`">Genre</RouterLink>
        <RouterLink :to="`/plateforme/${id}`">Plateforme</RouterLink>
        <RouterLink :to="`/support/${id}`">Support</RouterLink>
        <RouterLink :to="`/saga/${id}`">Saga</RouterLink>
    </div>
</template>