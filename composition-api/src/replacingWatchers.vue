<template>
    <div>
        <!-- Option API -->
        <input type="text" placeholder="Name" v-model="name">
    </div>
    <br><br>

       <div>
        <!-- Composition API -->
        <input type="text" placeholder="First Name" v-model="firstName">
        <input type="text" placeholder="Last Name" v-model="lastName">
    </div><br><br>

    <div>
        <!-- Reactive API -->
        <input type="text" placeholder="reactive First Name" v-model="FName">
        <input type="text" placeholder="reactive Last Name" v-model="LName">
        <input type="text" placeholder="reactive Hero Name" v-model="options.heroName">
    </div>
</template>

<script>
import { ref, watch, reactive, toRefs} from 'vue'

    export default {
        name: 'replacingWatchers',

        setup(){
            const firstName = ref('')
            const lastName = ref('Khan')


            const state = reactive({
                FName: '',
                LName: '',
                options: {
                    heroName: ''
                }
            })

        // replacing watchers with reactive API.
        watch(() => {
            return {...state}
        }, (newValue, oldValue) => {
            console.log('old FName : ', oldValue.FName)
            console.log('new FName : ', newValue.FName)
            console.log('old LName : ', oldValue.LName)
            console.log('new LName : ', newValue.LName)
        })


        watch(() => {
            state.options
        }, (newVal, oldVal) => {
            console.log('Old hero Name : ', oldVal)
            console.log('New hero Name : ', newVal)
        })


        // replacing watchers with composition API.
        // for multiple sources --->
        watch([firstName, lastName], (newValues, oldValues) => {
            console.log('First Name old Value : ', oldValues[0])
            console.log('First Name new Value : ', newValues[0])
            console.log('Last Name old Value : ', oldValues[1])
            console.log('Last Name new Value : ', newValues[1])

        }, {
            // immediate: true  // run the watcher to an initial value.
        })

            return{
                firstName,
                lastName,
                ...toRefs(state)
            }
        },

        data(){
            return{
                name: ''
            }
        },
        watch: {
            name(newValue, oldValue){
                console.log('old Value : ', oldValue)
                console.log('new Value : ', newValue)
            }
        }
    }
</script>

<style scoped>

</style>