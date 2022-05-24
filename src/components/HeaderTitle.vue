<script setup>
import { defineProps } from "vue";
const props = defineProps(["msg"]);
</script>

<template>
  <header>
    <h1>{{ props.msg }}</h1>
  </header>
</template>

<style lang="scss" scoped>
header {
  width: 100%;
  min-height: 75px;
  background: gray;

  h1 {
    color: white;
    text-align: center;
    line-height: 70px;
  }
}
</style>
