<template>
    <header class="header">
        <h1>记事本</h1>
        <input placeholder="请输入任务" class="new-todo" v-model="name" @keyup.enter="add">
        <button class="add" @click="add">添加任务</button>
    </header>
</template>

<script>
export default {
    data () {
        return {
            name: ''
        }
    },
    methods: {
        add () {
            this.$emit('addEvent', this.name)
            this.name = ''
        }
    }
}
</script>

<style>

</style>