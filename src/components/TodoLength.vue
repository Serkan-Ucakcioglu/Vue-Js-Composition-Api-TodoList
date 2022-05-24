<script setup>
import { defineProps } from "vue";

const props = defineProps(["todo"]);
</script>

<template>
  <div>
    <span v-show="todo">{{ props.todo }} Adet Todo Var.</span>
  </div>
</template>

<style lang="scss" scoped>
span {
  display: inline;
  margin-left: auto;
  border: 1px solid black;
  background: rgb(255, 170, 70);
  padding: 5px 30px;
  border-radius: 5px;
}
</style>
