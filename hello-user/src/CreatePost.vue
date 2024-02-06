<template>
 <form @submit.prevent="createPost">  <!-- to pevent the page relod. -->
    <div>
        <label for="id" class="label1">Post Id</label>
        <input type="text" id="id" class="a" v-model="sendRequest.id">
        <br>
    </div>
     <div>
        <label for="name" class="label2">Post Name</label>
        <input type="text" id="name" class="b" v-model="sendRequest.name">
         <br>
    </div>
     <div>
        <label for="body" class="label3">Post body</label>
        <input type="text" id="body" class="c" v-model="sendRequest.body">
         <br>
    </div>
    <button class="btn">Create Post</button>
 </form>
</template>

<script>
import axios from 'axios'

    export default {
        name: 'CreatePost',
        data(){
            return{
                sendRequest: {
                    id: '',
                    name: '',
                    body: ''
                }
            }
        },
        methods: {
            createPost(){
                axios.post('https://jsonplaceholder.typicode.com/posts', this.sendRequest)
                .then((response) => {
                    console.log(response)
                })
                .catch((error) => {
                    console.log(error)
                })
            }
        }
    }
</script>

<style scoped>
.a,.b,.c{
    margin: 10px;
    padding: 10px 30px;
    border-radius: 40px;
    border-color: aquamarine;
}
.a:hover{
    cursor: pointer;
    box-shadow: 1px 1px 1px 1px skyblue ;
}
.b:hover{
    cursor: pointer;
    box-shadow: 1px 1px 1px 1px skyblue;
}
.c:hover{
    cursor: pointer;
    box-shadow: 1px 1px 1px 1px skyblue;
}

.label1, .label2, .label3{
    font-size: 20px;
    color: black;
    margin-left: 100px;
    text-align: center;
}

.label1{
    margin-right: 35px;
}

.label3{
    margin-right: 12px;
}

.btn{
    font-size: 25px;
    margin-top: 90px;
    margin-left: 300px;
    border-radius: 40px;
    padding: 7px 20px;
    color: black;
    border-color: black;
    background: linear-gradient(140deg, skyblue, green);
}

.btn:hover{
    box-shadow: 2px 2px 2px 2px rgb(36, 34, 34);
}

</style>