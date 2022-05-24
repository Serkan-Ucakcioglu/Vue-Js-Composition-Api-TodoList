<script setup>
import HeaderTitle from "@/components/HeaderTitle.vue";
import TodoForm from "@/components/TodoForm.vue";
import TodoLength from "@/components/TodoLength.vue";
import TodoListData from "./components/TodoListData.vue";
import { computed, onMounted, provide, ref } from "vue";
import SendButtonVue from "./components/SendButton.vue";

const TodoList = ref([]);

onMounted(() => {
  if (localStorage.getItem("todosItem")) {
    let todosItem = JSON.parse(localStorage.getItem("todosItem"));
    todosItem.forEach((todo) => {
      TodoList.value.push(todo);
    });
  }
});

const addTodo = (todoText) => {
  if (todoText.length > 4) {

    TodoList.value.push({
      id: Date.now(),
      content: `${todoText}`,
    });
    localStorage.setItem("todosItem", JSON.stringify(TodoList.value));
  } else{ 
 
  }
};
const removeItem = (index) => {
  TodoList.value.splice(index, 1);
  localStorage.setItem("todosItem", JSON.stringify(TodoList.value));
};

const todos = computed(() => {
 if(TodoList.value.length > 0 ) {
     return TodoList.value.length
 }
});
</script>

<template>
  <HeaderTitle msg="Todo List Vue Js" />
  <TodoForm  @sends="addTodo" />
  <TodoListData @remove="removeItem" :mydata="TodoList" />
  <TodoLength  :todo="todos" />
</template>

<style lang="scss" scoped>
* {
  padding: 0;
  margin: 0;
}
</style>
