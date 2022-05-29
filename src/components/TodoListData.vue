<script setup>
import { ref, computed, watch } from "vue";

const props = defineProps(["mydata"]);
const emit = defineEmits(["remove"]);
const isActive = ref(true);
const send = (index) => emit("remove", index);
const evenFilter = computed(() => {
  return props.mydata.filter((check) => check == true);
});
</script>

<template>
  <ul>
    <li
      :class="{ active: todo.check == true ? isActive : false }"
      v-for="(todo, index) in mydata"
      :key="todo.id"
    >
      <input :id="todo.id" type="checkbox" v-model="todo.check" />
      <label :for="todo.id"> {{ todo.content }} </label>
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

    label {
      cursor: pointer;
    }
  }
}
.active {
  border: 2px solid rgb(233, 150, 122);
  color: #fff;
  background: rgb(233, 150, 122);
  text-decoration: line-through;
}
</style>
