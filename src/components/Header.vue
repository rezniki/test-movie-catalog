<template>
    <header class="header">
        <div class="logo">📽 MOOZ</div>
        <input v-model="searchQuery" @input="search" placeholder="Search..." class="search-input" />
        <div class="user">
        <span>Your Name</span>
        <div class="user-icon">👤</div>
        </div>
    </header>
</template>

<script setup>
import { ref } from 'vue';

const searchQuery = ref('');
const emit = defineEmits(['search']);

const search = () => {
    const app = getCurrentInstance().appContext.app.config.globalProperties;
    app.searchQuery = searchQuery.value;
    app.currentPage = 1;
    emit('search');
};
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
    font-size: 24px;
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