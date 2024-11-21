<template>
    <div>sum: {{ sum }}</div>
    <button @click="sumAdd1">点击sum + 1</button>
</template>

<script setup lang="ts" name="Person234">
    import {ref, watch} from 'vue'

    let sum = ref(10)

    function sumAdd1() {
        sum.value++
    }

    // 监听sum的变化 监视【ref】定义的基本类型数据
    const stopWatch = watch(sum, (newValue, oldValue) => {
        console.log(newValue, oldValue)
        if (newValue > 15) {
            // 停止监视
            stopWatch()
        }
    })

</script>
