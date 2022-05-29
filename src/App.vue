<script setup>
import HeaderTitle from "@/components/HeaderTitle.vue";
import TodoForm from "@/components/TodoForm.vue";
import TodoLength from "@/components/TodoLength.vue";
import TodoListData from "./components/TodoListData.vue";
import { computed, onMounted, watch, ref } from "vue";
import SendButtonVue from "./components/SendButton.vue";

const todoList = ref([]);

onMounted(() => {
  if (localStorage.getItem("todosItem")) {
    let todosItem = JSON.parse(localStorage.getItem("todosItem"));
    todosItem.forEach((todo) => {
      todoList.value.push(todo);
    });
  }
});

const addtodo = (todoText) => {
  if (todoText.length > 4) {
    todoList.value.push({
      id: Date.now(),
      content: `${todoText}`,
      check: false,
    });
    localStorage.setItem("todosItem", JSON.stringify(todoList.value));
  } else {
  }
};
const removeItem = (index) => {
  todoList.value.splice(index, 1);
  localStorage.setItem("todosItem", JSON.stringify(todoList.value));
};

const todos = computed(() => {
  if (todoList.value.length > 0) {
    return todoList.value.length;
  }
});
watch(
  todoList,
  () => {
    localStorage.setItem("todosItem", JSON.stringify(todoList.value));
  },
  { deep: true }
);
const filter = computed(() => {
  return todoList.value.filter((todo) => todo.check == true);
});
const filters = computed(() => {
  return todoList.value.filter((todo) => todo.check == false);
});
</script>

<template>
  <HeaderTitle msg="Todo List Vue Js" />
  <TodoForm @send="addtodo" />
  <TodoListData @remove="removeItem" :mydata="todoList" />
  <TodoLength :filters="filters" :filter="filter" :todo="todos" />
</template>

<style lang="scss" scoped>
* {
  padding: 0;
  margin: 0;
}
</style>
