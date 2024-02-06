<template>
<!-- Template refs made it possible to access DOM nodes directly within vue -->
    <div>
        <input type="text" ref="optionRef">
        <input type="text" ref="compositionRef">
    </div>
</template>

<script>
import { ref, onMounted } from 'vue'

    export default {
        name: 'replacingTemplateRefs',

        // refering using composition API.
        setup(){
            const compositionRef = ref(null)
            onMounted(() => {
                compositionRef.value.focus()
            })
            return{
                compositionRef
            }
        },

        // refering using options API.
        // mounted(){
        // this.$refs.optionRef.focus()
        // }
    }
</script>

<style scoped>

</style>