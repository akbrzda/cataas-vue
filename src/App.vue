<script setup>
import {ref} from 'vue';
const catText = ref('')


function getImgWithText() {
  const img = document.querySelector(".catImg");
  img.src = "https://cataas.com/cat/says/" + catText.value;
}

function getImgWithTag() {
  const img = document.querySelector(".catImg");
  img.src = "https://cataas.com/cat/" + catText.value;
}
</script>

<template>
  <div class="cat-block">
<input type="text" v-model="catText" id="#input"/>
<button @click="getImgWithText()">Press me if you want cats with your text</button>
<!-- <button @click="getImgWithTag()">Press me if you want cats with tag</button> -->
 <img  class="catImg"/>
 </div>
</template>

<style scoped>
.cat-block {
  display: flex;
  flex-direction: column;
  gap: 40px;
  align-items: center;
}
input {
  background-color: #fff;
  width: 400px;
  height: 40px;
  color: #000;
  border-color: #eee;
}
</style>
