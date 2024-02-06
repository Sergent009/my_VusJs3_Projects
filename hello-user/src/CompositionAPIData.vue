<template>
    <div>
        <h2> Options - {{ o_firstName }}</h2>
        <h2> Composition API - {{ c_firstName }}</h2>

        <h2>{{ greet }}</h2>
        <h2>{{ greetHero }}</h2>

        <!-- <h2>{{state.firstName}} {{state.lastName}}</h2> -->
        <h2>{{ reactiveGreetHero}}</h2>
    </div>
</template>

<script>
import { ref, reactive } from 'vue'
    export default {
         name: 'CompositionAPIData',
        // 1st method to replace data() object with composition API.
        // using ref method --->
        setup(){
            // ref is a function which returns a reactive and mutable object that serves as
            // a reactive reference to the internal value it is holding
            const c_firstName = ref('Mannan')
            const c_lastName = ref('Khan')
            const c_heroName = ref('Ertughrul Ghazi')
        
            const greet = `Hello ${c_firstName.value}`
            const greetHero = `Hello ${c_heroName.value} from ${c_firstName.value} ${c_lastName.value}`


            // 2nd method to replace data() object.
            // using reactive method --->
            const state = reactive({
                firstName: 'Abdul Mannan',
                lastName: 'Khan',
                hero: 'Engin Altan'
            })

            const reactiveGreetHero = `Nice to meet you ${state.hero} my name is ${state.firstName} ${state.lastName}`


            return{
                c_firstName,
                greet,
                greetHero,
                reactiveGreetHero
            }
        },

         data(){
        return{
            o_firstName: 'Abdul'
        }
    }
    }
</script>

<style scoped>

</style>