<template>
    <p>vue-vite 練習</p>
    {{data}}
    <input type="text" v-model='text'/>
    <p>輸出：{{text}}</p>
</template>

<script setup>
import {ref} from '@vue/reactivity'
    const data = '輸入：'
    const text = ref('')
</script>

<style scoped>
</style>
