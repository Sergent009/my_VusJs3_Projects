<template>
    <div>
        <h3>Child C - Component</h3>
        <h2>Using Inject - {{ username }}</h2>
        <h2>{{myAge}}</h2>
    </div>
</template>

<script>
    export default {
        name: 'ChildC',
        inject: ['username', 'myAge']
    }
</script>

<style scoped>

</style>