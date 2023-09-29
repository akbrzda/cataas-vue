<script setup>
import {ref} from 'vue';
import Tags from './components/Tags.vue';
const catText = ref('');
const types = ref(['random', 'gif',  'says', 'tags']);
const selectedType = ref('random'); // Default selected type


function getImgWithText() {
  const img = document.querySelector(".catImg");
  const test = document.querySelector(".test");
  const inputText = document.querySelector("#input");
  const constBuffer = Math.random();

  if (selectedType.value === 'says') {
    img.src = "https://cataas.com/cat/says/" + catText.value + "?cache=" + constBuffer;
  } else if(selectedType.value === 'random') {
    img.src = "https://cataas.com/cat" + catText.value + "?cache=" + constBuffer;
  } else if (selectedType.value === 'gif') {
    img.src = "https://cataas.com/cat/gif" + "?cache=" + constBuffer;
  } else if (selectedType.value === 'tags') {
    img.src = "https://cataas.com/cat/" + catText.value +  "?cache=" + constBuffer;
  } else {
    test.innerHTML = "Не сработало";
  }
}

</script>

<template>
  <div class="cat-block">
    <div class="types-block">
    <label v-for="(type) in types" :for="type" > {{ type.toUpperCase() }}
      <input  class="photo-type" type="radio" :value="type" name="type" :id="type" v-model="selectedType">
    </label>
  </div>
  <a href="tags.html" v-if="selectedType === 'tags'">Tags *Press Me*</a>
  <!-- <Tags v-if="selectedType === 'tags'"/> -->

    <div class="input-block">
      <input type="text" v-model="catText" id="#input" v-if="selectedType === 'says' || selectedType === 'tags'"/>
      <button @click="getImgWithText()" >Generate Photo</button>
    </div>
    
  </div>
  <img  class="catImg"/>
</template>
