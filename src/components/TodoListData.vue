<script setup>
import { ref, watch } from "vue";

defineProps(["mydata"]);
const emit = defineEmits(["remove"]);
const isActive = ref(true);
const send = (index) => emit("remove", index);

</script>

<template>
  <ul>
    <li
      :class="{ active: todo.check == true ? isActive : false }"
      v-for="(todo, index) in mydata"
      :key="todo.id"
    >
      <input type="checkbox" v-model="todo.check" />

      <input
        :class="{ bx: todo.show == true }"
        class="editInput"
        type="text"
        v-model="todo.title"
        :disabled="todo.show == false"
      />

      <label class="editBtn" @click="todo.show = true">Edit</label>
      <span v-if="todo.show">Edit-On</span>
      <button class="okBtn" @click="todo.show = false">ok</button>
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
    align-items: center;
    background: rgb(221, 221, 221);
    padding: 5px;
    margin-bottom: 15px;
    border-radius: 5px;
    height: 35px;

    .todoDelete {
      display: inline;
      padding: 5px;
      background: rgb(244, 67, 54);
      color: white;
      border: 2px solid white;
      border-radius: 5px;
      margin-left: auto;
      cursor: pointer;

      &:hover {
        background: red;
        border: 1px solid white;
        border-radius: 5px;
      }
    }

    .editInput {
      border-radius: 4px;
      background: none;
      padding: 8px;
      margin-left: 5px;
      color: rebeccapurple;
      font-size: 15px;
      font-weight: bold;
    }
  }
}
.bx {
  border: 2px solid #0168d9;
}
.okBtn {
  padding: 5px;
  background-color: #0168d9;
  color: #fff;
  margin-left: 15px;
  border-radius: 4px;
  height: 35px;
  cursor: pointer;
}
.editBtn {
  padding: 2px;
  background-color: #e7e7e7;
  color: black;
  margin-left: 10px;
  margin-right: 5px;
  border-radius: 4px;
  height: 30px;
  line-height: 30px;
  border: 2px solid black;
  cursor: pointer;
}
.active {
  border: 2px solid rgb(233, 150, 122);
  background: #d5f198;
  text-decoration: underline;
}
</style>
