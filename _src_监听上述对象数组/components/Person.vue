<template>
    <div>
        <div>name: {{ person.name }}</div>
        <div>age: {{ person.age }}</div>
        <button @click="changeName">修改名字</button>
        <button @click="changeAge">修改年龄</button>
        <button @click="changePerson">修改人</button>
        <button @click="changeCar">修改车</button>
    </div>
</template>

<script setup lang="ts" name="Person234">
    import {reactive, watch} from 'vue'

    let person = reactive({
        name: '张三',
        age: 18,
        car: {
            brand: '宝马',
            price: 10000
        }
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
    function changeCar (){
        person.car = {
            brand: '奔驰',
            price: 20000
        }
    }
    // 情况五：监听上述对象数组，可以对多个数据进行监视，监视的是对象地址，若要监视对象内部数据的变化，需要开启deep属性
    watch([()=>person.car,()=>person.name], (newValue, oldValue) => {
        console.log(newValue, oldValue)
    }, {deep: true})
</script>
