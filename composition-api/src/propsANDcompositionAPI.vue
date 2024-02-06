<template>
    <div>
        <input type="text" placeholder="First Name" v-model="firstName">
        <input type="text" placeholder="Last Name" v-model="LastName">
    </div>

    <greetingUSINGprops :firstName="firstName" :LastName="LastName" @callHero="callHero" />
</template>

<script>
import { ref } from 'vue'
import greetingUSINGprops from './greetingUSINGprops.vue'

    export default {
        name: 'propsANDcompositionAPI',
        components: {
            greetingUSINGprops
        },
        setup(){
            const firstName = ref('')
            const LastName = ref('')

            // receiving a custom event from a child event to a parent event.
            function callHero(hero){
                alert(`Calling ${hero}`)
            }

            return {
                firstName,
                LastName,
                callHero
            }
        }
        
    }
</script>

<style scoped>

</style>