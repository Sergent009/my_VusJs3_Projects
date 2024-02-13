<template>
<div class="container">
    <input type="text" class="inputField" v-model="currentTask" placeholder="Enter the task..">
    <button class="taskbuttons" v-show="!isEditing" @click="addTask">Add Task</button>
    <button class="taskbuttons" v-show="isEditing" @click="taskEdited">Edit Task</button>

    <div v-show="!isEditing" class="alltasks" v-for="(allTasks, index) in tasks" :key="index">
        {{allTasks}}
        <button @click="editTask(index)" class="editButton">Edit Task</button>
        <button @click="deleteTask(index)" class="deleteButton">Delete Task</button>
    </div>  

    <div v-show="isEditing"></div> 
</div>
</template>


<script>
export default {
name: 'todoApp',

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
    /* box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1)
                0 2px 4px -1px rgba(0, 0, 0, 0.06); */
}

.taskbuttons{
    width: 90px;
    height: 41px;
    position: absolute;
    top: 40px;
    left: 867px;
    border-radius: 5px;
}

</style>



