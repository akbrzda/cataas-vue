<script setup>
import { ref } from 'vue'

async function tags() {
  const requestURL =
    "https://cataas.com/api/tags";
  const request = new Request(requestURL);

  const response = await fetch(request);
  const tagsListJson = await response.json();

  tagsList(tagsListJson);
}
function tagsList(obj) {
  const mainSection = document.querySelector(".card");
  const tagsJsonList = obj;
  const myList = document.createElement("ul");
  for (const tag of tagsJsonList) {
    const listItem = document.createElement("li");
    listItem.textContent = tag;
    myList.appendChild(listItem);
  }
  mainSection.appendChild(myList);
}

tags();
</script>

<template>
  <div class="card">
  </div>
</template>