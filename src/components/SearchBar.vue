<template>
    <div class="search-bar" v-if="searchQuery">
        <p class="search-phrase">You searched for: {{ searchQuery }}</p>
        <p class="results-count" v-if="totalResults">{{ totalResults }} results</p>
    </div>
</template>

<script setup>
defineProps(['searchQuery', 'totalResults']);
</script>

<style scoped>
.search-bar {
    padding: 20px;
    text-align: center;
    background-color: #f9f9f9;
    border-bottom: 1px solid #ddd;
}

.search-phrase {
    font-size: 18px;
    font-weight: bold;
    color: #333;
    margin-bottom: 5px;
}

.results-count {
    font-size: 16px;
    color: #1e90ff; 
    margin-top: 0;
}
</style>