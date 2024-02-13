<template>
<div class="container">
    <input type="text" class="inputField" v-model="currentTask" placeholder="Enter the task..">
    <button class="taskbuttons" v-show="!isEditing" @click="addTask">Add Task</button>
    <button class="taskbuttons" v-show="isEditing" @click="taskEdited">Edit Task</button>

    <div class="semi-container">
    <div v-show="!isEditing" class="alltasks" v-for="(allTasks, index) in tasks" :key="index">
        <!-- <arrow /> -->
        
        {{allTasks}}
        <button @click="editTask(index)" class="editButton">Edit Task</button>
        <button @click="deleteTask(index)" class="deleteButton">Delete Task</button>
    </div>  

    <div v-show="isEditing"></div> 
    </div>
</div>
</template>


<script>
// import arrow from '../assets/arrow-right-long-solid.svg'

export default {
name: 'todoApp',

// components: {
//      arrow
// },

data(){
    return{
        currentTask: '',
        tasks: [],
        isEditing: false
    }
},

methods: {
    addTask(){
        this.tasks.push(this.currentTask)
        this.currentTask = ''
    },

    deleteTask(index){
      this.tasks.splice(index, 1)  
    },

    editTask(index){
        this.isEditing = true
        this.currentTask = this.tasks[index]
        
    },

    taskEdited(index){
        this.isEditing = false
        this.tasks.splice(index, 1)
        this.tasks.push(this.currentTask)
        this.currentTask = ''
    }
}
}
</script>

<style scoped>

.container{
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
}

.inputField{
    width: 600px;
    height: 35px;
    position: absolute;
    top: 40px;
    left: 350px;
    border-radius: 5px;
    border: none;
    background: #ebebeb;
    border: 1px solid black;
    border-radius: 6px;
    font-size: 17px;
    /* box-shadow: 0px 4px 6px -1px rgba(0, 0, 0, 0.1)
                0px 2px 4px -1px rgba(0, 0, 0, 0.06); */
}

.taskbuttons{
    width: 90px;
    height: 41px;
    position: absolute;
    top: 39px;
    left: 867px;
    border-radius: 5px;
    background: white;
   color: green;
   font-weight: 600;
   border: 1px solid black;
}

.semi-container{
    position: relative;
    top: 150px;
    left: 350px;
    width: 570px;
    height: auto;
    background: #ebebeb;
    border: 1px solid rgb(63, 62, 62);
    border-radius: 10px;
    padding: 20px;
}

.alltasks{
    padding: 10px 10px;
    font-size: 17px;
}

.editButton{
   position: absolute;
   left: 405px;
   background: white;
   color: green;
   font-weight: 600;
   width: 90px;
   height: 30px;
   border: none;
   border-radius: 5px;
}
.editButton:hover{
    background: rgb(130, 150, 100);
    color: black;
}
.deleteButton{
    position: absolute;
   left: 500px;
   background: white;
   color: green;
   font-weight: 600;
   width: 90px;
   height: 30px;
   border: none;
   border-radius: 5px;
}
.deleteButton:hover{
    background: rgb(130, 150, 100);
    color: black;
}

</style>



