<template>
    <div>
         <h1 @mouseover="incrementBy1">Hovered {{ count }} Times</h1>
    </div>
</template>

<script>
import MixinsCounter from './mixins/counter.js'
    export default {
        name: 'HoverCounter',
    mixins: [MixinsCounter]
    }
</script>

<style scoped>

</style>