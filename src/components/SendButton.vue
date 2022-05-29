<script setup>
defineProps(["isDisabled"]);
const emit = defineEmits(["send"]);
const send = () =>  emit("send");

</script>
<template>
  <div>
    <button :disabled="isDisabled" @click="send">Button</button>
  </div>
</template>

<style lang="scss" scoped>
button {
  display: flex;
  align-items: center;
  height: 40px;
  padding: 5px;
  background: #2196f3;
  cursor: pointer;
  color: white;
  border-radius: 5px;
}
</style>
