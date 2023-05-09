<template>
    <h1>vue-vite 練習</h1>
    <button @click="changeView(1)">顯示單向綁定</button>
    <button @click="changeView(2)">顯示雙向綁定</button>
    <button @click="changeView(3)">v-for</button>
    <button @click="changeView(4)">computed</button>
    <button @click="changeView(5)">watch</button>
    <button @click="changeView(12)">神秘按鈕</button>

    <div class="container-1" v-if="view === 1">
    
        <h1>單向綁定</h1>
    </div>

    <div class="container-2" v-if="view === 2">
        <h1>多項綁定</h1>
        {{data}} <input type="text" v-model='text'>
        <p>輸出：{{text}}</p>
    </div>

    <div v-if="view === 3">
        <p class="test-cls" 
            :key="test"
            >{{test}}</p>
        <p
            v-for = "(value, index) in dataList" 
            :key="value"
            >
            <span class="hint" v-show="key !== 'key3'">{{index+1}}. {{ value }}</span>
        </p>
    </div>

    <div v-if="view === 4">
        <h1>Computed 計算屬性</h1>
        <input type="number" v-model="num" />
        <h3>{{ numFormat }}</h3>
    </div>

    <div v-if="view === 5">
        <h1>watch 監聽器</h1>
        <input type='text' :style="dymanicStyle"  v-model = 'txt'>

    </div>

    <div v-if="view !== 1 && view !== 2 && view !== 3 && view !== 4 && view !== 5" >
        <h1>空</h1>
    </div>


</template>

<script setup>
import { computed,reactive,ref, watch, watchEffect } from 'vue';

    const data = '輸入：'
    const text = ref('test')
    const view = ref(1)
    const changeView = (index) => {
        view.value = index
    }

    const test = ref('test')
    const dataList = [
        'a',
        'b',
        'c',
    ]

    setTimeout(() => {
        test.value = 'apple'
    }, 2000);

    const num = ref(0)
    const numFormat = computed(() => {
        
        if(Number.isNaN(num.value * 100)) return num
        return `${num.value * 100}%`
    })

    const txt = ref('')

    // watch(() => txt.value, 
    //(newData, oldData) => {
    //    console.log(newData, oldData)
    //})

    const dymanicStyle = reactive ({
            color:'red',
            fontSize: '14px',
            transition: 'ease-in-out 0.2s'
        })

    watch(txt, (newData) => {
        if(newData.length % 2 === 0) {
            dymanicStyle.color = 'skyblue'
            dymanicStyle.fontSize = '20px'
        } else {
            dymanicStyle.color = 'red'
            dymanicStyle.fontSize = '14px'
        }
    })

    const stop = watchEffect(() => {
        if(txt.value === 'stop') stop()
    })
    
</script>

<style scoped>
    .container-1 {
        border: 2px red solid;
    }
    .container-2 {
        border: 2px  skyblue solid;
    }
    .test-cls {
        font-size: 40px;
        animation: openIn 1s ease-in-out;
    }

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
