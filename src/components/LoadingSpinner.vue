<template>
    <div class="spinner"></div>
</template>

<style scoped>
.spinner {
    border: 4px solid #f3f3f3;
    border-top: 4px solid #1e90ff;
    border-radius: 50%;
    width: 40px;
    height: 40px;
    animation: spin 1s linear infinite;
    margin: 20px auto;
}

@keyframes spin {
    0% { transform: rotate(0deg); }
    100% { transform: rotate(360deg); }
}
</style>