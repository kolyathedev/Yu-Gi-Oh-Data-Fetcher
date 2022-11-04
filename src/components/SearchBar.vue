<template>
  <div>
    <label for="card-search" class="sr-only">Search for a Yu-Gi-Oh card</label>
    <input
      name="card-search"
      id="searchBar"
      @input="onChange"
      placeholder="Search for a card"
      @keyup.enter="$emit('searchEvent', search)"
    />

    <button @click="$emit('searchEvent', search)">Search</button>
  </div>
</template>
<script setup lang="ts">
import { ref } from "vue";
import type { Ref } from "vue";

const search: Ref<string | number> = ref("");
function onChange(event: Event) {
  search.value = (event.target as HTMLInputElement).value;
  console.log(search.value);
}
</script>
<style scoped lang="scss">
#searchBar {
  width: 90%;
  height: 60%;
  padding: 10px;
  place-self: center;
}

div {
  button {
    width: 60%;
    height: 60%;
    justify-self: center;
    color: white;
    background: hsla(160, 100%, 37%, 1);
    border-radius: 5px;
    transition: 0.3s ease-in-out;
    font-weight: bold;

    &:hover {
      background: rgba(0, 189, 126, 0.699);
    }
  }
}
</style>
