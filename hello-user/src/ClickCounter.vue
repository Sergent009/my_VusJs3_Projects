<template>
    <div>
        <button @click="incrementBy1">Clicked {{ count }} Times</button>
    </div>
</template>

<script>
import CounterMixins from './mixins/counter.js'

    export default {
        name: 'ClickCounter',
        data(){
        return{
            count: 100
        }
        },
        mixins: [CounterMixins]

    }
</script>

<style scoped>

</style>