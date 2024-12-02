<script>
export default {
  data() {
	return {
		newItem: 'пропишите ваше дело',
    items: [],
  }
  },


methods: {
	addItem: function() {
		this.items.push(this.newItem);
	}
}

}

</script>

<template>
  <h1>Чек-лист</h1>

  <h2>Список запланированных дел</h2>

  <ul>
    <li v-for="(item,index) in items" :key="index">
      <input type="checkbox" name="" id=""></input>
      <label for="task1"> {{ newItem }} </label>
      <button type="button">Редактировать</button>
      <button type="button">Удалить задачу</button>
    </li>



    <li><button @click="addItem" type="button">Добавить задачу</button></li>

  </ul>

</template>

<style>

</style>
