<script setup>
import { ref} from "vue";

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

      <label class="editBtn" @click="todo.show = true">✍</label>
      <span v-if="todo.show">Edit-On</span>
      <button class="okBtn" @click="todo.show = false">✓</button>
      <button @click="send(index)" class="todoDelete">🗑️</button>
    </li>
  </ul>
</template>

<style lang="scss" scoped>
ul {
  display: flex;
  flex-direction: column;
  align-items: center;

  li {
    width: 93%;
    display: flex;
    align-items: center;
    background: #fff;
    padding: 5px;
    margin-bottom: 20px;
    border-radius: 5px;
    height: 40px;
    box-shadow: rgba(0, 0, 0, 0.35) 0px 5px 15px;

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
      font-size: 15px;
    }
  }
}
.bx {
  border: 2px solid #074383;
}
.okBtn {
  padding: 8px;
  background-color: #4b91dc;
  color: #fff;
  margin-left: 15px;
  border-radius: 4px;
  height: 35px;
  cursor: pointer;
}
.editBtn {
  font-size: 20px;
  padding: 3px;
  background-color: #e7e7e7;
  color: black;
  margin-left: 10px;
  margin-right: 5px;
  border-radius: 4px;
  height: 26px;
  line-height: 30px;
  border: 2px solid black;
  cursor: pointer;
}
.active {
  background: #b4bfd0;
  color: red;
}

@media screen and (max-width: 375px) {

}
</style>
