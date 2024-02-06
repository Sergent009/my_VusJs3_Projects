<template>
    <div>
        <!-- To fetch the data on button click. -->
        <!-- <button @click="getPost">Load Post</button> -->
    
    <h3 v-if="getError">{{getError}}</h3>
    <div v-for="post in posts" :key="post.id">
        <h3>{{post.id}}. {{post.title}}</h3>
        <p>{{post.body}}</p>
        <hr />
    </div>
    </div>
</template>

<script>
import axios from 'axios'
    export default {
        name: 'PostList',
        // To fetch the data on page relod.
        created(){
            this.getPost()
        },
        data(){
            return{
                posts: [],
                getError: ''
            }
        },
        methods: {
            getPost(){
                axios.get('https://jsonplaceholder.typicode.com/posts')  // making the get request.
                .then((response) => {
                console.log(response.data)
                this.posts = response.data
            })
            .catch((error)=>{
                    console.log('Cannot load posts : ' + error)
                    this.getError = 'receiving Error in retreiving Data !.'
            })
            }
        }
    }
</script>

<style scoped>

</style>