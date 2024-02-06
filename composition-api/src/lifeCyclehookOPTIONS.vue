<template>
     <!-- Lifecycle hooks are a window into how the library
    you are using works behind the scenes. Lifecycle hooks
     allow you to know when your component is created, added
      to the DOM, updated, or destroyed. This article will
       introduce you to the creation, mounting, updating,
        and destruction hooks in Vue. js. -->
        <div></div>
</template>

<script>
    export default {
        name: 'lifeCyclehookOPTIONS',

        data(){
            return{
              
            }
            
        },
        beforeMount(){
            console.log("beforeMount() -- Options")
        },
        mounted(){
            console.log("mounted() -- Options")
        }
    }
</script>

<style scoped>

</style>