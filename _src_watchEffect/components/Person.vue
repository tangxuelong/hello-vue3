<template>
    <div>
        <div>需求：当水温达到60度，或者水位超过80cm，给服务器发请求</div>
        <div>水温：{{ waterTemperature }}</div>
        <div>水位：{{ waterLevel }}</div>
        <button @click="changeWaterTemperature">修改水温</button>
        <button @click="changeWaterLevel">修改水位</button>
    </div>
</template>

<script setup lang="ts" name="Person234">
    import {ref, watchEffect} from 'vue'

    let waterTemperature = ref(10)
    let waterLevel = ref(10)

    function changeWaterTemperature (){
        waterTemperature.value += 10
    }

    function changeWaterLevel (){
        waterLevel.value += 10
    }

    // watch([waterTemperature, waterLevel], (value) => {
    //     let [waterTemperature, waterLevel] = value

    //     if (waterTemperature >= 60 || waterLevel >= 80){
    //         console.log('请求服务器')
    //     }
    // })

    watchEffect(()=>{
        if (waterTemperature.value >= 60 || waterLevel.value >= 80){
            console.log('请求服务器')
        }
    })
</script>
