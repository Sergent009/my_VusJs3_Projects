<template>
<!-- V Model and Composition API -->
    <div>
        <input type="text" placeholder="First Name(data)" v-model="FName">
        <input type="text" placeholder="Last Name(data)" v-model="LName">
        <br><br>
    </div>
        <input type="text" placeholder="heroName(ref)" v-model="heroName">
        <br><br>
        <input type="text" placeholder="First Name(reactive)" v-model="firstName">
        <input type="text" placeholder="Last Name(reactive)" v-model="lastName">
</template>

<script>
import { ref, reactive, toRefs} from 'vue'
    export default {
        name: 'VModel',

        setup(){
            let heroName = ref('')

            const state = reactive({
                firstName: '',
                lastName: ''
            })

            return {
                heroName,
                ...toRefs(state)
            }
        },


        data(){
            return{
                FName: '',
                LName: ''
            }
        }
    }
</script>

<style scoped>

</style>