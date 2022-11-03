<template>
  <div>
    <label for="searchBar">
      Search for a card
      <input id="searchBar" @input="onChange" placeholder="Search for a card" />
      <button @click="$emit('someClickEvent', search)">Search</button>
    </label>
  </div>
</template>
<script setup lang="ts">
import { ref } from "vue";
import type { Ref } from "vue";

const search: Ref<string | number> = ref("");
function onChange(event: Event) {
  search.value = (event.target as HTMLInputElement).value;
}
</script>
<style lang="scss"></style>
