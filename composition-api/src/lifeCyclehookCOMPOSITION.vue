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
import{onBeforeMount, onMounted} from 'vue'
    export default {
        name: 'lifeCyclehookCOMPOSITION',

        setup(){
            onBeforeMount(() => {
                console.log("onBeforeMount()  -- Composition")
            })
            onMounted(() => {
                console.log("onMounted() -- Composition")
            })
        }
    }
</script>

<style scoped>

</style>