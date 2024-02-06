<template>

<h2>{{firstName}} {{lastName}}</h2>

</template>

<script>
import { reactive , toRefs} from 'vue'

    export default {
        name: 'DemoTwo',
        setup(){
            const state = reactive({
                firstName: 'Abdul Mannan',
                lastName: 'Khan'
            })

           setTimeout(() => {
                state.firstName = 'Engin'
                state.lastName = 'Altan'
           }, 2000)

           return toRefs(state)
        }
    }
</script>

<style scoped>

</style>