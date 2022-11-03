<script setup lang="ts">
import DisplayCard from "../components/DisplayCard.vue";
import { ref } from "vue";
import SearchBar from "@/components/SearchBar.vue";

const displayCardToggle = ref<boolean>(true);
function clickMe(n: string): void {
  console.log(n);
}
</script>

<template>
  <div class="container">
    <section><SearchBar @some-click-event="(n) => clickMe(n)" /></section>

    <DisplayCard id="display" />

    <button>Save To Deck Collection</button>
  </div>
  <!-- Key and Mouse Modifiers to Events -->
  <!--
    <button @click.right="hide">Hide</button>
    <input @keyup.space="left" />
  -->
</template>
<style scoped lang="scss">
.container {
  display: grid;

  // grid-template-columns: repeat(3, 1fr);
  // fr being a fraction of the free space in the grid.
  // grid-template-rows: repeat(3, 300px);
  // grid-template-areas:
  //   ". search ."
  //   ". card ."
  //   ". button .";

  // column-gap: 10px;
  // row-gap: 20px;
  // same as:
  gap: 30px 20px;

  // aligns items in center of their cell along the row axis
  // justify-items: center; --> taken care of by place-items: center;
  // justify-items: start;
  // stretches item to whole width of cell - default
  // justify-items: stretch;
  // justify-items: end;

  // aligns items on column axis
  // align-items: center; --> taken care of by place-items: center;
  // align-items: center;
  // align-items: baseline;
  // align-items: stretch;

  // place-items: center;

  // interestingly justify-content: and align-content: actually move the entire grid within the container...
  // align-content: start;
  // justify-content: space-evenly;
  // can also shortcut with place-content: ;
  // place-content: space-between;

  // Grid shortcut
  // grid: grid-template-rows: ;/ grid-template-columns: ; insert grid areas as below.
  grid:
    " . search ." 1fr
    "card card card" 600px
    ". button ." 1fr / 0.5fr 3fr 0.5fr;
  background: #ffffff;
}

section {
  grid-area: search;
  align-self: start;
  background: #1f3657;
}
#display {
  background: #b47a57;
  grid-area: card;
  border: #1f3657 solid 10px;
  border-radius: 5px;
}
button {
  background: rgb(0, 0, 0);
  color: white;
  grid-area: button;
  padding: 10px;
  border-radius: 3px;
  cursor: pointer;
  transition: 0.3s ease-in-out;

  &:hover {
    background: rgb(19, 18, 18);
  }
}
</style>
