<template>
    <div class="container">
        <div class="upperbox">My Todo App || Mannan Khan</div>
        <div class="typeTask">
            <input type="text" id="searchbar" placeholder="Type Task..." v-model="taskSearch">
            <button id="addbutton" @click="addTask" >Add Task</button>
        </div>
        <div class="showTasks" v-for="task in tasks" :key="task.id">
            {{ task }}
        </div>
    </div>
</template>

<script>
    export default {
        name: 'TodoAppNew',

        data(){
            return{
                taskSearch: '',
                tasks: []
            }
        },
        methods: {
            addTask(){
                this.tasks.push(this.taskSearch)
                this.taskSearch = ''
            }
        }
    }
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Teko:wght@300;600&display=swap');

.container{
    position: absolute;
    top: 0;
    left: 0;
    background: #313131;
    width: 100%;
    height: 100%;
}

.upperbox{
    width: 100%;
    height: 7%;
    background: white;
    font-size: 37px;
    color: #2b2a2a;
    font-family: 'Teko', sans-serif;
    font-weight: bolder;
}

.typeTask{
    width: 100%;
    height: 20%;
    position: absolute;
}

#searchbar{
    position: absolute;
    top: 50px;
    left: 330px;
    width: 500px;
    height: 30px;
    border-radius: 3px;
    font-size: 17px;
}

#addbutton{
    position: absolute;
    top: 51px;
    left: 837px;
    width: 100px;
    height: 36px;
    border-radius: 3px;
    font-size: 17px;
}

</style>