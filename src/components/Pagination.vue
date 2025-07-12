<template>
    <div class="pagination">
        <button :disabled="currentPage === 1" @click="$emit('change-page', currentPage - 1)">Previous</button>
        <button
        v-for="page in totalPages"
        :key="page"
        @click="$emit('change-page', page)"
        :disabled="page === currentPage"
        :class="{ active: page === currentPage }"
        >
        {{ page }}
        </button>
        <button :disabled="currentPage === totalPages" @click="$emit('change-page', currentPage + 1)">Next</button>
    </div>
</template>

<script setup>
defineProps(['totalPages', 'currentPage']);
defineEmits(['change-page']);
</script>

<style scoped>
.pagination {
    display: flex;
    justify-content: center;
    gap: 10px;
    padding: 20px;
}

.pagination button {
    padding: 5px 10px;
    border: 1px solid #1e90ff;
    background-color: #fff;
    border-radius: 3px;
    cursor: pointer;
}

.pagination button:disabled {
    background-color: #f0f0f0;
    cursor: not-allowed;
}

.pagination button.active {
    background-color: #1e90ff;
    color: #fff;
}
</style>