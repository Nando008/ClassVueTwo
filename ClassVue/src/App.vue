<script setup>
  import { ref } from 'vue';

  let newTask = ref('')

  let taskList = ref([
  {
    name: 'estudiar',
    done: true
  }, 
  {
    name: 'comer',
    done: false
  },  
  {
    name: 'dormir',
    done: false
  } 
])

  function setDone(index){
    taskList.value[index].done = true
  }

  function addtask(){
    if(newTask.value.trim() === '')return
    taskList.value.push({
      name: newTask.value,
      done: false
    })
    newTask.value = ''
  }

</script>

<template>
  <div class="container">
    <h1>to-do list</h1>
    <p class="subtitle">{{ newTask }}</p>
  
    <div>
      <div class="task" :class="{done: task.done}" v-for="(task, index) in taskList" :key="index">{{ task.name }} <span class="button" @click="setDone(index)">x</span></div>
    </div>

    <input @keypress.enter="addtask" v-model="newTask" type="text" placeholder="Escriba su tarea">
    <p v-show="newTask != ''" class="help">Presiona enter para agregar la tarea</p>
  </div>
</template>

<style scoped>
  .container {
    color: rgb(245, 241, 235);
    padding: 6px 12px;
    background-color: rgb(5, 146, 146);
    border-radius: 6px;
    max-width: 420px;
    margin: 0px auto;
    font-family: Edu TAS Beginner;
  }

  h1 {
    text-transform: uppercase;
    text-align: center;
    font-size: 18px;
    margin: 0;
    margin-top: 12px;
  }
  .subtitle {
    font-size: 10px;
    margin-bottom: 16px;
    text-align: center;
    opacity: 0.6;
  }

  .task {
    display: flex;
    justify-content: space-between;
    background-color: rgb(121, 221, 221);
    border-radius: 3px;
    margin-bottom: 1px;
    padding: 2px 2px 2px 6px;
  }

  .task:hover {
    background-color: rgb(10, 69, 178, 0.8);
  }

  .button {
    background-color: rgba(254, 3, 3, 0.756);
    display: inline-block;
    border-radius: 3px;
    padding: 0 6px;
    
  }

  .button:hover {
    cursor: pointer;
    background-color: red;
  }

  input {
    border: none;
    border-radius: 3px;
    padding: 2px 6px;
    outline: none;
    width: 100%;
    box-sizing: border-box;
    width: 100%;
    margin-top: 12px;
  }

  .help{
    margin: 0%;
    font-size: 8px;
    opacity: 0.6;
  }

  .done{
    text-decoration: line-through;
  }
</style>
