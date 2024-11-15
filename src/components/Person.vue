<template>
    <div>{{ name }}</div>
    <div>{{ age }}</div>
    <button @click="changeName">修改名字</button>
    <button @click="changeAge">修改年龄</button>
    <button @click="lookTel">查看手机号</button>
</template>

<script setup lang="ts" name="Person234">
    let name = '张三'
    let age = 18
    function changeName() {
        name = '李四'
    }
    function changeAge() {
        age = 20
    }
    function lookTel() {
        alert('123456789')
    }
</script>
