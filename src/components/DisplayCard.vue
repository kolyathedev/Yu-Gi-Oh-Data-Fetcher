<script setup lang="ts">
import Card from "./Card.vue";

const props = defineProps<{
  name: string;
  atk?: number;
  def?: number;
  level?: number;

  desc?: string;
}>();
</script>

<template>
  <Card :title="name" :stats="[atk, def]" :level="level" :desc="desc" />
</template>
