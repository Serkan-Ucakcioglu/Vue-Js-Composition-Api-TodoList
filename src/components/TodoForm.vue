<script setup>
import { ref, computed, watch } from "vue";
import SendButton from "@/components/SendButton.vue";

const todoText = ref("");
const emit = defineEmits("send");

let isDisabled = computed(() => {
  return todoText.value.length > 4 ? false : true;
});
const send = () => {
  emit("send", todoText.value);
  todoText.value = "";
};

let error = ref(false);
let inputSuccess = ref(true);

const sends = () => {
  if (todoText.value.length < 4) {
    return (error.value = true), (inputSuccess.value = false);
  } else {
    send();
    return (inputSuccess.value = true), (error.value = false);
  }
};
</script>

<template>
  <section>
    <div class="todo-form">
      <input
        v-model.trim="todoText"
        @keyup.enter="sends"
        placeholder="Write Your Todo ?"
        :class="{ error, inputSuccess }"
        class="todoInput"
        type="text"
        required
      />
      <SendButton :isDisabled="isDisabled" @send="send" />
    </div>
  </section>
</template>

<style lang="scss" scoped>
section {
  padding: 10px;
  margin-bottom: 10px;
  box-sizing: border-box;

  .todo-form {
    display: flex;
    justify-content: center;

    .todoInput {
      margin-right: 10px;
      width: 92%;
      height: 35px;
      border: 2px solid #fff;
      border-radius: 5px;
      outline: none;
    }

    .error {
      border: 2px solid red;
    }

    .inputSuccess {
      border: 2px solid rgb(25, 81, 25);
    }
  }
}
</style>
