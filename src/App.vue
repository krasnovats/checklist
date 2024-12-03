<template>
  <section class="container">
    <div class="main_box">
      <h1>Список задач</h1>
       <input v-model="newTask" type="text" class="form_input" placeholder="Введите новую задачу" @keyup.enter="addTask">
      
      
       <ul class="check_box">
       <li v-for="(task, index) in tasks" :key="index">
         <p class="item" :class="{completed: task.completed}">{{ task.text }}</p>
         <div class="buttons"> 
           <button @click="toggleTask(index)">{{ task.completed ? "Готово" : 'Не готово' }}</button>
           <button @click="editTask(index)">Править</button>
           <button @click="removeTask(index)">Удалить</button>
         </div>
       </li>
      </ul>
 
 
    </div>
  </section>
 
 </template>
 
 <script>
 export default {
   data() {
     return {
       tasks: [], // Массив дел
       newTask: '', // Переменная для нового дела
     }
   },
   methods: {
     addTask () {
       if (this.newTask) {
         this.tasks.push({ text: this.newTask, completed: false}); // Добавляем новое дело
         this.newTask = ''; // Очищаем поле ввода
       }
     },
     removeTask (index) {
       this.tasks.splice(index, 1); // Удаляем дело по индексу
     },
     editTask (index) {
       const updateTask = prompt('Редактировать задачу:', this.tasks[index].text);
       if (updateTask !== null) {
         this.tasks[index].text = updateTask; // Обновляем текст дела
       }
     },
     toggleTask(index){
       this.tasks[index].completed = !this.tasks[index].completed // Переключаем статус выполнения
     }
 
     }
   }
 
 
 </script>
 
 
 <style>
 .completed {
   text-decoration: line-through;
 }
 
 </style>
 