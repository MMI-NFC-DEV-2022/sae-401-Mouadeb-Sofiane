<script setup lang="ts">
import { useRoute } from 'vue-router/auto';
import { defineProps } from 'vue';
import { supabase } from '@/supabase';
const route = useRoute('/celebrite/[id]');
import type { Database, Tables } from '@/supabase-types';
defineProps <Database["public"]["Tables"]["Celebrite"]["Row"] & {CFilms:Tables<'Films'>[]} & {Genre:Tables<'Genre'>[]} & {Saga:Tables<'Saga'>[]} & {Variante:Tables<'Variante'>} & {Support:Tables<'Support'>} & {Plateforme:Tables<'Plateforme'>}>()
</script>

<template>
    <div class="p-5 bg-pink-100">
        <div>
            <h1 class="text-center text-6xl mb-16 mt-16">{{ prenom_celebrite }} {{ nom_celebrite }}</h1>
                <div class="flex gap-4">
                <img :src="photo_celebrite" class="object-cover rounded-md w-56">
            
                <div class="flex flex-col">
                    <div class="flex pb-2">
                        <p class="text-l underline">Nationnalité</p>
                        <p class="ml-5 text-justify">{{ nationnalite_celebrite }}</p>

                        <p class="text-l ml-10 underline">Date de naissance</p>
                        <p class="ml-5">{{ date_naissance }}</p>
                    </div>
                    
                    <div class="flex mt-10 pb-2">
                        <p class="text-l underline">Biographie</p>
                        <p class="ml-5  text-justify">{{ bio_celebrite }}</p>
                    </div>
                    <div class="flex pb-2">
                        
                    </div>  
                </div>
            </div>
        </div>
    </div>
</template>