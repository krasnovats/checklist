<template>
  <div>
    <h1>Чеклист</h1>
    <input v-model="newTask" placeholder="Добавьте новое дело" @keyup.enter="addTask" />
    <ul>
      <li v-for="(task, index) in tasks" :key="index">
        <span :class="{ completed: task.completed }">{{ task.text }}</span>
        <button @click="toggleTask(index)">{{ task.completed ? 'Не выполнено' : 'Выполнено' }}</button>
        <button @click="editTask(index)">Редактировать</button>
        <button @click="removeTask(index)">Удалить</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTask: '', // Переменная для нового дела
      tasks: [], // Массив дел
    };
  },
  methods: {
    addTask() {
      if (this.newTask) {
        this.tasks.push({ text: this.newTask, completed: false }); // Добавляем новое дело
        this.newTask = ''; // Очищаем поле ввода
      }
    },
    removeTask(index) {
      this.tasks.splice(index, 1); // Удаляем дело по индексу
    },
    toggleTask(index) {
      this.tasks[index].completed = !this.tasks[index].completed; // Переключаем статус выполнения
    },
    editTask(index) {
      const updatedTask = prompt("Редактировать дело:", this.tasks[index].text);
      if (updatedTask !== null) {
        this.tasks[index].text = updatedTask; // Обновляем текст дела
      }
    },
  },
};
</script>

<style>
.completed {
  text-decoration: line-through; /* Перечеркивание текста выполненных дел */
}
</style>