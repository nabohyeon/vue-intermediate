<template>
  <div class="inputBox shadow">
		<input type="text" v-model="addTodo" v-on:keyup.enter="addTodoList">
		<!-- <button v-on:click="addTodoList">add</button> -->
		<span class="addContainer" v-on:click="addTodoList">
				<i class="fas fa-plus addBtn"></i>
		</span>
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
			if (this.addTodo !== '') {
                this.$emit('addTodoItem', this.addTodo)
				this.clearInput()
			}
		},
		clearInput : function () {
			this.addTodo = ""
		}
	}
}
</script>

<style scoped>
    input:focus{
        outline: none;
    }
    .inputBox{
        background: white;
        height: 50px;
        line-height: 50px;
        border-radius: 5px;
    }
    .inputBox input{
        border-style: none;
        font-size: 0.9rem;
    }
    .addContainer{
        float: right;
        background: linear-gradient(to right, #6478fb, #8763fb);
        display: block;
        width: 3rem;
        border-radius: 0 5px 5px 0;
    }
    .addBtn{
        color: white;
        vertical-align: middle;
    }
</style>