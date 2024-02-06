<template>
    <div>
        <h3>Child A - Component</h3>
        <childB />
    </div>
</template>

<script>
import ChildB from './ChildB.vue'

    export default {
        name: 'ChildA',

        components: {
            ChildB
        }
    }
</script>

<style scoped>

</style>