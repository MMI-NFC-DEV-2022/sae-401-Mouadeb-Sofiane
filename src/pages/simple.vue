<script setup lang="ts">
import AfficheFilm from '@/components/AfficheFilm.vue';
import type { SchemaFilms } from '@/types';

    const monFilm :SchemaFilms = {
        titre_film: "Titre du film",
        note_film: 5,
        description_film: "Ceci est une description du film",
        image_film: "\public\pexels-binyamin-mellish-106399.jpg",
    };
</script>

<template>
    <div class="grid grid-cols-3 gap-4">
        <AfficheMFilm :nom-film="monFilm.titre_film" :note="monFilm.note_film" :description="monFilm.description_film" :image_projet="monFilm.image_film" />
    </div>
    <AfficheFilm titre-film="Titre du film" :favori="true" image_film="\pexels-binyamin-mellish-106399.jpg"/>
</template>