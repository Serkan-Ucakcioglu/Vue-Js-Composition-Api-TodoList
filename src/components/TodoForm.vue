<script setup>
import { defineEmits, ref ,defineProps} from "vue";
import SendButton from "@/components/SendButton.vue";
const todoText = ref("");
const emit = defineEmits("onsends");

const onsends = () => {
  emit("onsends", todoText.value);
  todoText.value = "";
};
</script>

<template>
  <section>
    <div class="todo-form">
      <input
        v-model="todoText"
        @keydown.enter="sends"
        placeholder="Todo Write Please"
        class="todoInput"
        type="text"
      />
      <SendButton   @les="onsends" />
     
    </div>
  </section>
</template>

<style lang="scss" scoped>
section {
  padding: 10px;
  background: rgb(173, 150, 150);
  margin-bottom: 10px;
  box-sizing: border-box;

  .todo-form {
    display: flex;
    width: 100%;

    .todoInput {
      margin-right: 10px;
      flex: 1;
      height: 35px;
      border: 2px solid #fff;
      border-radius: 5px;
    }
  }
}
</style>
