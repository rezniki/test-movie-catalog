<template>
  <div class="container">
    <header-component v-model:search-query="searchQuery" @search="handleSearch" />
    <search-bar :search-query="searchQuery" :total-results="totalResults" />
    <loading-spinner v-if="isLoading" />
    <no-results v-if="!isLoading && movies.length === 0 && searchQuery" />
    <movie-list :movies="movies" />
    <pagination
      :total-pages="totalPages"
      :current-page="currentPage"
      @change-page="changePage"
    />
    <div v-if="error" class="error">{{ error }}</div>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import HeaderComponent from './components/Header.vue';
import SearchBar from './components/SearchBar.vue';
import MovieList from './components/MovieList.vue';
import Pagination from './components/Pagination.vue';
import LoadingSpinner from './components/LoadingSpinner.vue';
import NoResults from './components/NoResults.vue';

const movies = ref([]);
const searchQuery = ref('');
const currentPage = ref(1);
const totalPages = ref(0);
const totalResults = ref(0);
const isLoading = ref(false);
const error = ref('');

const fetchMovies = async () => {
  if (!searchQuery.value) return;
  isLoading.value = true;
  error.value = '';
  try {
    const response = await fetch(
      `https://www.omdbapi.com/?apikey=8523cbb8&s=${encodeURIComponent(searchQuery.value)}&page=${currentPage.value}`
    );
    const data = await response.json();
    console.log('API Response:', data); // Для отладки
    if (data.Response === 'True') {
      movies.value = data.Search || [];
      totalResults.value = parseInt(data.totalResults);
      totalPages.value = Math.ceil(totalResults.value / 10);
    } else {
      movies.value = [];
      totalResults.value = 0;
      totalPages.value = 0;
      error.value = data.Error || 'No results found';
    }
  } catch (err) {
    console.error('Fetch error:', err);
    error.value = 'Failed to fetch data. Check API key or network.';
    movies.value = [];
    totalResults.value = 0;
    totalPages.value = 0;
  } finally {
    isLoading.value = false;
  }
};

const handleSearch = (query) => {
  searchQuery.value = query;
  currentPage.value = 1;
  fetchMovies();
};

const changePage = (page) => {
  currentPage.value = page;
  fetchMovies();
};
</script>

<style scoped>
.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0;
  font-family: Arial, sans-serif;
  background-color: #f9f9f9;
}

.error {
  color: red;
  text-align: center;
  padding: 10px;
}
</style>