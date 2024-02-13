<template>
<div class="container">
    <input type="text" class="inputField" v-model="currentTask" placeholder="Enter the task..">
    <button class="taskbuttons" v-show="!isEditing" @click="addTask">Add Task</button>
    <button class="taskbuttons" v-show="isEditing" @click="taskEdited">Edit Task</button>

    <div class="semi-container">
    <div v-show="!isEditing" class="alltasks" v-for="(allTasks, index) in tasks" :key="index">        
        {{allTasks}}
        <button @click="editTask(index)" class="editButton">Edit Task</button>
        <button @click="deleteTask(index)" class="deleteButton">Delete Task</button>
    </div>  

    <div v-show="isEditing"></div> 
    </div>
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

<style>
body {
  font-family: 'Arial', sans-serif;
  background-color: #f8f9fa;
}

.container {
  max-width: 600px;
  margin: auto;
  background-color: #fff;
  padding: 20px;
  border-radius: 10px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

.inputField {
  width: calc(100% - 16px);
  padding: 8px;
  font-size: 16px;
  margin-bottom: 10px;
  border: 1px solid #ced4da;
  border-radius: 5px;
}

.taskbuttons {
  padding: 10px;
  font-size: 16px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  transition: background-color 0.3s;
}

.taskbuttons:hover {
  background-color: #007bff;
  color: #fff;
}

.add-btn {
  background-color: #28a745;
}

.edit-btn {
  background-color: #17a2b8;
}

.alltasks {
  margin-bottom: 10px;
  padding: 15px;
  border: 1px solid #ccc;
  border-radius: 5px;
  background-color: #fff;
  display: flex;
  justify-content: space-between;
  align-items: center;
  transition: transform 0.3s;
}

.alltasks:hover {
  transform: scale(1.02);
}

.task-buttons button {
  padding: 8px;
  margin-left: 5px;
  font-size: 12px;
  cursor: pointer;
  border: none;
  border-radius: 5px;
  transition: background-color 0.3s;
}

.task-buttons button:hover {
  background-color: #dc3545;
  color: #fff;
}

.editing-task {
  margin-bottom: 10px;
  padding: 15px;
  border: 1px solid #ccc;
  border-radius: 5px;
  background-color: #fff;
}
</style>





