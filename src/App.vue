<script setup lang="ts">
import { RouterLink, RouterView } from "vue-router";
import { ref } from "vue";
const deckName = ref();
const sizeIcons = ref("3x");
</script>

<template>
  <header>
    <h3 v-if="deckName">{{ deckName }}</h3>
    <nav>
      <RouterLink class="link" to="/">
        <font-awesome-icon icon="fa-solid fa-magnifying-glass" size="3x" />
      </RouterLink>
      <RouterLink class="link" to="/deckView"
        ><font-awesome-icon icon="fa-solid fa-box-archive" size="3x" />
      </RouterLink>
      <RouterLink class="link" to="/about"
        ><font-awesome-icon icon="fa-solid fa-circle-question" size="3x"
      /></RouterLink>
    </nav>
  </header>

  <RouterView />
</template>

<style scoped>
header {
  line-height: 1.5;
  max-height: 100vh;

  display: grid;
  grid: 1fr 3fr 1fr / 1fr 3fr 1fr;
}

nav {
  min-width: 100%;
  height: auto;
  font-size: 12px;
  text-align: center;
  margin-top: 2rem;

  grid-row-start: 2;
  grid-column-start: 2;
  display: grid;
  grid: repeat(3, 1fr) / repeat(3, 1fr);
  border-radius: 5px;
  border: #454647 solid 5px;
}
.link {
  place-self: center;
}
</style>
