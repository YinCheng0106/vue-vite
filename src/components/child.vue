<template>
    <div>
        字數：{{ msgCount }}
    </div>
</template>

<script setup>
import { computed } from '@vue/reactivity'
import { watch } from 'vue'
const props = defineProps(['data_1'])

const emit = defineEmits(['update'])

const msgCount = computed(() => {
    return props.data_1.length
})

watch(msgCount, (newValue) => {
    emit('update', newValue)
})
</script>

<style scoped>

</style>