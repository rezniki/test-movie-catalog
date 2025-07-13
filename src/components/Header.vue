<template>
    <header class="header">
        <div class="logo">📽 MOOZ</div>
        <input v-model="searchQuery" @input="debouncedSearch" placeholder="Search..." class="search-input" />
        <div class="user">
        <div class="user-icon">👤</div>
        <span>Your Name</span>
        </div>
    </header>
</template>

<script setup>
import { ref } from 'vue';
import { debounce } from 'lodash';

const searchQuery = ref('');
const emit = defineEmits(['search']);

// Debounce поиск, чтобы избежать частых запросов
const debouncedSearch = debounce(() => {
    emit('search', searchQuery.value);
}, 500);
</script>

<style scoped>
.header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 20px;
    background-color: #fff;
    border-bottom: 1px solid #ddd;
}

.logo {
    font-size: 28px;
    font-weight: bold;
    color: #1e90ff;
}

.search-input {
    padding: 10px;
    font-size: 16px;
    border: 1px solid #ddd;
    border-radius: 5px;
    width: 300px;
}

.user {
    display: flex;
    align-items: center;
    gap: 10px;
}

.user-icon {
    font-size: 20px;
}
</style>