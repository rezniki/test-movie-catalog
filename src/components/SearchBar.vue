<template>
    <div class="search-bar">
        <p>You searched for: {{ searchQuery }}</p>
        <p v-if="totalResults"> {{ totalResults }} results</p>
    </div>
</template>

<script setup>
import { ref } from 'vue';

const searchQuery = ref('');
const totalResults = ref(0);

defineProps(['searchQuery', 'totalResults']);
</script>

<style scoped>
.search-bar {
    padding: 20px;
    text-align: center;
    color: #666;
}

.search-bar p {
    margin: 5px 0;
}

.search-bar p:first-child {
    font-weight: bold;
}

.search-bar p:last-child {
    color: #1e90ff;
    font-size: 14px;
}
</style>