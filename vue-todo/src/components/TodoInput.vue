<template>
  <div>
      <input type="text" v-model="addTodo">
      <button v-on:click="addTodoList">add</button>
  </div>
</template>

<script>
export default {
    data : function () {
        return {
            addTodo : ""
        }
    },
    methods : {
        addTodoList : function () {
            localStorage.setItem(this.addTodo, this.addTodo);
            this.addTodo = "";
        }
    }
}
</script>

<style>

</style>