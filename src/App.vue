<script setup>
import componentA from './components/componentA.vue'
</script>

<template>
  <h1>vue-vite 練習</h1>
  <componentA></componentA>
  <footer>vue3+vite 學習中</footer>
</template>

<style scoped>
    h1 {
        animation: openIn 1s ease-in-out;
    }

    @keyframes openIn{
        0% {
            opacity: 0;
            transform: translateY(20px);
        }
        100% {
            opacity: 1;
            transform: translateY(0);
        }
    }
</style>
