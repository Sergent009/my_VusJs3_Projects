<template>
    <div>
       <h2> {{ name }} </h2>
       <button @click="ChangeName">Change Name</button>
       <hr />
    </div>
    <div>
       <h1> {{ count }} </h1>
       <button @click="incrementCount">Increment</button>
       <hr />
    </div>
    <div>
        <h2>{{firstName}} {{lastName}}</h2>
        <button @click="changeHeroName">Change Actor Name</button>
    </div>

</template>

<script>
import { ref, reactive, toRefs } from 'vue'
    export default {
        name: 'ReplacingMethods',
        setup(){
            let  count = ref(0)

            const state = reactive({
                firstName: 'Bruce',
                lastName: 'Wayne'
            })

            function incrementCount(){
                count.value += 1
            }

            function changeHeroName(){
                state.firstName = 'Engin'
                state.lastName = 'Altan'
            }



            return {
                count,
                incrementCount,
                ...toRefs(state),
                changeHeroName
            }
        },



        data(){
            return{
                name: 'Abdul Mannan Khan'
            }
        },
        methods: {
            ChangeName(){
                this.name = 'Bruce Wayne'
            }
        }
    }
</script>

<style scoped>

</style>