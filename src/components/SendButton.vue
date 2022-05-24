<script setup>
import { ref, defineEmits } from "vue";
const todoText = ref("");
const emit = defineEmits(["les"]);
const send = () => {
emit("les", todoText.value);

};



</script>
<template>
  <div>
   <button  @click="send">Button</button>

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
.disabled{

}
</style>
