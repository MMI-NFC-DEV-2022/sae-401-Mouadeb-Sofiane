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
        <h1 class="text-center text-4xl">{{ titre_film }}</h1>
        
    <div class="flex gap-4">
    <img :src="image_film" class="rounded-xl" /> <!-- Placer l'image à gauche -->
    <div>
        <div class="flex flex-col">
            <div class="flex pb-2">
            <p class="text-l underline">Date de sortie du film</p>
            <p class="text-l ml-5">{{ date_film }}</p>
        </div>
        <div class="flex pb-2">
            <p class="text-l underline">Durée du film</p>
            <p class="text-l ml-10">{{ temps_film }}</p>
        </div>
        <div class="flex">
            <p class="underline">Note du film</p>
            <div class="flex ml-8 pl-2 pb-2">
                <div v-for="n in note_film ?? 0" class="text-gray-200">
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
        <div class="flex">
            <h2 class="underline">Genre du film</h2>
                <p v-for="unGenre in Genre" class="ml-5">{{ unGenre.genre_film }}</p>
        </div>
        </div>
        <h2 class="mt-5 underline">Synopsis </h2>

    <p>{{ description_film }}</p>
    <h2 class="mt-5 underline">Acteurs </h2>
    <div class="flex gap-1">
        <RouterLink :to="`/celebrite/${id}`" class="flex gap-8">
                <div v-for="uneCelbrite in Celebrite">
                    <img :src="uneCelbrite.photo_celebrite" class="rounded-full w-24" alt="Photo Acteurs">
                </div>
        </RouterLink>
    </div>
    </div>
</div>
<div> 
</div>
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


    <div class="max-w-md mx-auto bg-white shadow-md rounded-md p-4">
    <!-- Header de l'interface -->
    <div class="flex items-center justify-between mb-4">
        <h2 class="text-xl font-semibold">Commentaires</h2>
        <button class="text-blue-500 hover:text-blue-700">Ajouter un commentaire</button>
    </div>

    <!-- Section des commentaires -->
    <div class="space-y-4">
        <!-- Commentaire 1 -->
        <div class="flex items-center">
            <img src="../assets/img/avatar.jpg" alt="Avatar" class="w-10 h-10 rounded-full mr-4">
            <div>
                <h3 class="font-semibold">Utilisateur 1</h3>
                <p class="text-gray-600">Lorem ipsum dolor sit amet, consectetur adipiscing elit.</p>
            </div>
        </div>

        <!-- Commentaire 2 -->
        <div class="flex items-center">
            <img src="../assets/img/avatar.jpg" alt="Avatar" class="w-10 h-10 rounded-full mr-4">
            <div>
                <h3 class="font-semibold">Utilisateur 2</h3>
                <p class="text-gray-600">Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.</p>
            </div>
        </div>

        <!-- Commentaire 3 -->
        <div class="flex items-center">
            <img src="../assets/img/avatar.jpg" alt="Avatar" class="w-10 h-10 rounded-full mr-4">
            <div>
                <h3 class="font-semibold">Utilisateur 3</h3>
                <p class="text-gray-600">Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.</p>
            </div>
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