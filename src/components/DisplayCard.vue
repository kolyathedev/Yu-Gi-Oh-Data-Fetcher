<script setup lang="ts">
import Card from "./Card.vue";
import axios from "axios";
import { ref, reactive } from "vue";

const data = reactive({
  heading: "Ghost Sister & Spooky Dogwood",
  atk: 100,
  def: 200,
  level: 3,
  img: "ghostSister.png",
  desc: "During either turn...",
});
</script>

<template>
  <Card
    :title="data.heading"
    :stats="[data.atk, data.def]"
    :level="data.level"
    :img="data.img"
    :desc="data.desc"
  />
</template>
