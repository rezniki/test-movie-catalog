<template>
    <div class="movie-list">
        <movie-card v-for="movie in movies" :key="movie.imdbID" :movie="movie" />
    </div>
</template>

<script setup>
defineProps(['movies']);
</script>

<style scoped>
.movie-list {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
    gap: 20px;
    padding: 20px;
}
</style>