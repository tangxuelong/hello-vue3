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
    // 情况四：监视【reactive】定义的对象类型数据上的属性 需要监听一个getter函数，开启deep属性
    watch([()=>person.car,()=>person.name], (newValue, oldValue) => {
        console.log(newValue, oldValue)
    }, {deep: true})
</script>
