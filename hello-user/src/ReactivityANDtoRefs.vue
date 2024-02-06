<template>
    <div>
       <h2>{{name}}</h2>
    </div>
</template>

<script>
import { ref} from 'vue'
    export default {
        name: 'MannanKhan',
        setup(){
            /* When we use simple let and const to store a value vue doesn't know how to react
               to changes in the value. */
            // let name = 'Mannan Khan'

            /* On the other hand, ref lets the vue know that the value is changed. */
            const name = ref('Mannan Khan')
            

            setTimeout(() => {
                name.value = 'Aslam Khan'
                console.log(name)
            }, 2000)
            

            return{
                name
            }
        }
    }
</script>

<style scoped>

</style>