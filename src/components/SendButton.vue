<script setup>
import { ref, defineEmits, inject, defineProps } from "vue";

const props = defineProps(["isDisabled"]);

const emit = defineEmits(["send"]);
const send = () => {
  emit("send");
};
const buttonName = inject("buttonName");

//
</script>
<template>
  <div>
    <button :disabled="props.isDisabled" @click="send">{{ buttonName }}</button>
  </div>
</template>

<style lang="scss" scoped>
button {
  display: flex;
  align-items: center;
  height: 40px;
  padding: 5px;
  background: #2196f3;
  color: white;
  border-radius: 5px;
}
</style>
