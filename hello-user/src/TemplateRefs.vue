<template>
    <div>
        <input type="text" ref="inputRef" />
        <PostList />
    </div>
</template>
 
<script>
import PostList from './PostList.vue'
    export default {
        name: 'TemplateRefs',
        components:{
            PostList
        },
            //  Because the component is mounted, we 
            //  can access the properties that belong to 
            //  the component instance such as data or computed
        mounted(){
            this.$refs.inputRef.focus()
        }
    }
</script>

<style scoped>

</style>