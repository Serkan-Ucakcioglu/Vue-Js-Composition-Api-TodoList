<script setup>
import { defineProps, defineEmits } from "vue";
const props = defineProps(["mydata"]);
const emit = defineEmits(["remove"]);
const send = (index) => {
  emit("remove", index);
};
</script>

<template>
 <ul>
    <li v-for="(todo, index) in mydata" :key="todo.id" >
    {{ todo.content }}
    <button @click="send(index)" class="todoDelete">Delete</button>
  </li>
 </ul>
</template>

<style lang="scss" scoped>
ul {
  display: flex;
  flex-direction: column;

  li {
  display: flex;
  justify-content: space-between;
  align-items: center;
  background: rgb(221, 221, 221);
  color: black;
  padding: 5px;
  margin-bottom: 15px;
  border-radius: 5px;
  height: 35px;

  .todoDelete {
    padding: 5px;
    background: rgb(244, 67, 54);
    color: white;
    border: 2px solid white;
    border-radius: 5px;

    &:hover {
      background: red;
      border: 1px solid white;
      border-radius: 5px;
    }
  }
}
}

</style>
