<script setup lang="ts">
import { defineProps } from 'vue';
import type { Database, Tables } from '@/supabase-types';
defineProps <Database["public"]["Tables"]["Films"]["Row"] & {Celebrite:Tables<'Celebrite'>[]} & {Genre:Tables<'Genre'>[]} & {Saga:Tables<'Saga'>[]} & {Variante:Tables<'Variante'>} & {Support:Tables<'Support'>} & {Plateforme:Tables<'Plateforme'>}>()
</script>
<template>
    <RouterLink :to="`/maisons/${id}`">
        <div class="p-4 max-w-sm">
            <div class="flex rounded-lg h-full dark:bg-white bg-teal-400 p-8 flex-col">
                <div class="flex items-center mb-3">
                    <img :src="image_film" alt="Placeholder Image" class="w-40 h-70 rounded-lg object-cover object-center mb-6">
                </div>
            </div>     
        </div>
    </RouterLink>
</template>
