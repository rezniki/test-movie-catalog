<template>
    <div class="movie-card">
        <img v-if="movie.Poster !== 'N/A'" :src="movie.Poster" :alt="movie.Title" />
        <div v-else class="placeholder">No Poster</div>
        <div class="info">
        <h3>{{ movie.Title }}</h3>
        <p>Year: {{ movie.Year }}</p>
        <p>ID: {{ movie.imdbID }}</p>
        <p>Type: {{ movie.Type }}</p>
        </div>
    </div>
</template>

<script setup>
defineProps(['movie']);
</script>

<style scoped>
.movie-card {
    border: 2px solid #1e90ff;
    border-radius: 5px;
    overflow: hidden;
    text-align: center;
    background-color: #fff;
}

.movie-card img {
    width: 100%;
    height: 200px;
    object-fit: cover;
}

.placeholder {
    width: 100%;
    height: 200px;
    background-color: #f0f0f0;
    display: flex;
    align-items: center;
    justify-content: center;
    color: #666;
}

.info {
    padding: 10px;
}

.info h3 {
    font-size: 16px;
    margin-bottom: 5px;
}

.info p {
    font-size: 14px;
    color: #666;
}
</style>