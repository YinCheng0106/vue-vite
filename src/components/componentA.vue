<template>
    <button v-on:click="changeView(1)">顯示單向綁定</button>
    <button v-on:click="changeView(2)">顯示雙向綁定</button>
    <button @click="changeView(12)">神秘按鈕</button>


    <div class="container-1" v-if="view === 1">
        <h1>vue-vite 練習</h1>
        <p>單向綁定</p>
        {{data}}
    </div>

    <div class="container-2" v-if="view === 2">
        <p>多項綁定</p>
        <input type="text" v-model='text'>
        <p>輸出：{{text}}</p>
    </div>

    <div v-if="view !== 1 && view !== 2">
        <h1>空</h1>
    </div>

</template>

<script setup>
import {ref} from '@vue/reactivity'
    const data = '輸入：'
    const text = ref('')
    const view = ref(1)
    const changeView = (index) => {
        view.value = index
    }
</script>

<style scoped>
    .container-1 {
        border: 2px red solid;
    }
    .container-2 {
        border: 2px  skyblue solid;
    }
</style>
