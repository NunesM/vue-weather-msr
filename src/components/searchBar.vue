<template>
    <div class="search-box">
        <input 
        type="text"  
        class="search-bar" 
        placeholder="Pesquise a cidade..."
        v-model = "query"
        @keypress = "fetchWeather"
        />
    </div>
</template>

<style>
    @import "../assets/css/App.css";
</style>

<script>
    import '../assets/js/App.js';
</script>