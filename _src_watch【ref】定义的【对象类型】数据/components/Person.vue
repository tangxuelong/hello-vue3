<template>
    <div>
        <div>name: {{ person.name }}</div>
        <div>age: {{ person.age }}</div>
        <button @click="changeName">修改名字</button>
        <button @click="changeAge">修改年龄</button>
        <button @click="changePerson">修改人</button>
    </div>
</template>

<script setup lang="ts" name="Person234">
    import {ref, watch} from 'vue'

    let person = ref({
        name: '张三',
        age: 18
    })

    function changeName (){
        person.value.name += '~'
    }

    function changeAge (){
        person.value.age += 1
    }
    function changePerson (){
        person.value = {
            name: '李四',
            age: 20
        }
    }
    // 情况二：监视【ref】定义的对象类型数据，监视的是对象地址，若要监视对象内部数据的变化，需要开启deep属性
    watch(person, (newValue, oldValue) => {
        console.log(newValue, oldValue)
    }, {
        deep: true
    })
</script>
