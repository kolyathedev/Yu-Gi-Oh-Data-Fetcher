<script setup lang="ts">
export interface Props {
  title: string;
  stats?: (number | undefined)[];
  level?: number;
  img?: string;
  desc?: string;
}

const props = withDefaults(defineProps<Props>(), {
  title: "...",
  stats: () => [0, 0],
});
</script>

<template>
  <div class="container1">
    <h3>{{ title }}</h3>
    <div id="level">
      <img src="./star.png" alt="Star level image" v-for="n in level" />
    </div>
    <img
      id="mainImage"
      src="./ghostSister.png"
      alt="Ghost Sister and Spooky Dogwood"
    />
    <p class="description">
      {{ desc }}
    </p>
    <div class="stats">
      <p>{{ stats[0] }}</p>
      <p>{{ stats[1] }}</p>
    </div>
  </div>
</template>
<style scoped lang="scss">
.container1 {
  display: grid;
  grid-template-columns: 100%;
  grid-template-rows: 50px 100px 200px auto 50px;
  grid-template-areas:
    "title"
    "level1"
    "mainImg "
    "description"
    "stats";

  color: black;
  justify-content: center;
}

h3 {
  grid-area: title;
  background: rgb(255, 0, 0);
}

#level {
  grid-area: level1;
  background: #000;

  img {
    width: 20px;
    height: 20px;
  }
}

img {
  grid-area: mainImg;
  max-width: 100%;
  max-height: 100%;
}
#mainImage {
  border: solid 8px rgb(94, 94, 94);
}

.description {
  grid-area: description;
  border-bottom: solid 2px black;
  border: solid 3px rgb(77, 42, 18);
  background: #eed4bd;
}

.stats {
  grid-area: stats;
}
</style>
