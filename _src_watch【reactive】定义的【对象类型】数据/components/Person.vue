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
    import {reactive, watch} from 'vue'

    let person = reactive({
        name: '张三',
        age: 18
    })

    function changeName (){
        person.name += '~'
    }

    function changeAge (){
        person.age += 1
    }
    function changePerson (){
        Object.assign(person, {
            name: '李四',
            age: 20
        })
    }
    // 情况三：监视【reactive】定义的对象类型数据，默认监视的是对象内部数据的变化，不需要开启deep属性
    watch(person, (newValue, oldValue) => {
        console.log(newValue, oldValue)
    })
</script>
