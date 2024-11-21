<template>
    <div>{{ person.name }}</div>
    <div>{{ person.age }}</div>
    <div>{{ nameAge }}</div>
    <button @click="changeName">修改名字</button>
    <button @click="changeAge">修改年龄</button>
</template>

<script setup lang="ts" name="Person234">
    import {reactive, toRefs, toRef, computed} from 'vue'

    let person = reactive({
        name: '张三',
        age: 18
    })

    let {name, age} = toRefs(person)

    let _age2 = toRef(person, 'age')
    console.log(_age2)

    function changeName() {
        name.value = '李四'
    }

    function changeAge() {
        age.value = 20
    }

    let nameAge = computed(() => {
        return person.name + person.age
    })

</script>
