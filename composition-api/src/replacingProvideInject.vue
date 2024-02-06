<template>
    <div>
        <h2>Name - {{ name }}</h2>
        <ChildA />
    </div>
</template>

<script>
import ChildA from './ChildA.vue'
    export default {
        name: 'replacingProvideInject',

        components: {
            ChildA
        },

        data(){
            return{
                name: 'Abdul Mannan Khan',
                age: '18'
            }
        },

        provide(){
            return{
            username: this.name,
            myAge: this.age
            }
        }
    }
</script>

<style scoped>

</style>