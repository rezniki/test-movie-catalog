<template>
    <div class="pagination">
        <button :disabled="currentPage === 1" @click="$emit('change-page', currentPage - 1)">Previous</button>
        <button
        v-for="page in visiblePages"
        :key="page"
        @click="$emit('change-page', page)"
        :disabled="page === currentPage || typeof page === 'string'"
        :class="{ active: page === currentPage && typeof page !== 'string' }"
        >
        {{ page }}
        </button>
        <button :disabled="currentPage === totalPages" @click="$emit('change-page', currentPage + 1)">Next</button>
    </div>
</template>

<script setup>
import { computed } from 'vue';

const props = defineProps(['totalPages', 'currentPage']);
defineEmits(['change-page']);

// Логика для отображения 5 видимых страниц с "..." для пропусков
const visiblePages = computed(() => {
    const range = 2; // Количество страниц по обе стороны от текущей
    const pages = [];
    let start = Math.max(1, props.currentPage - range);
    let end = Math.min(props.totalPages, props.currentPage + range);

  // Если страниц мало, показываем все или последние 5
    if (end - start < 4 && props.totalPages > 5) {
        start = Math.max(1, props.totalPages - 4);
        end = props.totalPages;
    }

    for (let i = start; i <= end; i++) {
        pages.push(i);
    }

  // Добавляем первую страницу, если она не в диапазоне
    if (start > 2) {
        pages.unshift(1);
        if (start > 3) pages.splice(1, 0, '...');
    }

  // Добавляем последнюю страницу, если она не в диапазоне
    if (end < props.totalPages - 1) {
        if (end < props.totalPages - 2) pages.push('...');
        pages.push(props.totalPages);
    }

    return pages;
});
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

.pagination button:disabled:not(.active) {
    border: none;
    background: none;
    cursor: default;
    color: #666;
}
</style>