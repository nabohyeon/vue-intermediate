<template>
  <div>
      <ul>
        <li v-for="(todoItem, index) in propsdata" v-bind:key="todoItem.item" class="shadow">
          <i class="checkBtn fas fa-check" v-bind:class="{checkBtnCompleted: todoItem.complete}" 
					v-on:click="toggleComplete(todoItem, index)"></i>
          <span v-bind:class="{textCompleted: todoItem.complete}">{{todoItem.item}}</span>
          <span class="removeBtn" v-on:click="removeTodo(todoItem, index)">
            <i class="fas fa-trash-alt"></i>
          </span>
        </li>
        <!-- <li>1</li>
        <li>2</li>
        <li>3</li> -->
      </ul>
  </div>
</template>

<script>
export default {
  props: ['propsdata'],
  methods: {
    removeTodo: function (todoItem, index) {
      console.log(index)
      localStorage.removeItem(todoItem)
      this.todoItems.splice(index, 1) //index번째 배열에서 1개를 지우고 새로반환
    },
    toggleComplete: function (todoItem, index) {
			console.log(index)
      todoItem.complete = !todoItem.complete
			//로컬스토리지 데이터 갱신
			localStorage.removeItem(todoItem.item)
			localStorage.setItem(todoItem.item, JSON.stringify(todoItem))
    }
  }
}
</script>

<style scoped>
  ul{
    list-style-type: none;
    padding-left: 0px;
    margin-top: 0px;
    text-align: left;
  }
  li{
    display: flex;
    min-height: 50px;
    height: 50px;
    line-height: 50px;
    margin: 0.5rem 0;
    padding: 0 0.9rem;
    background: white;
    border-radius: 5px;
  }
  .checkBtn{
    line-height: 45px;
    color: #62acde;
    margin-right: 5px;
  }
  .removeBtn{
    margin-left: auto;
    color: #de4343;
  }
  .checkBtnCompleted{
    color: #b3adad;
  }
  .textCompleted{
    text-decoration: line-through;
    color: #b3adad;
  }
</style>