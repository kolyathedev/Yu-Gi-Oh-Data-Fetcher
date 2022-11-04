<script setup lang="ts">
import DisplayCard from "../components/DisplayCard.vue";
import { ref } from "vue";
import SearchBar from "@/components/SearchBar.vue";
import axios from "axios";

const data = ref({
  name: "",
  atk: 0,
  def: 0,
  level: 1,
  desc: ".....",
});
// const { name } = data.value;
// if we destructure as above we lose the reactivity

// const data2 = {
//   name: ref("ddd"),
// };
// // lets try pulling the vals from data2
// let { name } = data2;
// // we can pull data from an object with refs when the values are refs.

async function search(n: string): Promise<void> {
  try {
    console.log(n);
    let res = await axios.get(
      `https://db.ygoprodeck.com/api/v7/cardinfo.php?name=${n}`
    );
    console.log(res);
    data.value = res.data.data[0];

    console.log(data.value.atk);
  } catch (error) {
    console.error(error);
  }
}
</script>

<template>
  <div class="container">
    <SearchBar id="searchComp" @search-event="(n) => search(n)" />
    <!-- no need to write .value because of top-level ref unwrapping in templates -->
    <DisplayCard
      id="display"
      :name="data.name"
      :atk="data.atk"
      :def="data.def"
      :level="data.level"
      :desc="data.desc"
    />

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
  gap: 20px;
  grid: 1fr 5fr 1fr / 2fr 5fr 2fr;
  // background: #353535;
  // fr being a fraction of the free space in the grid.

  // grid-template-areas:
  //   ". search ."
  //   ". card ."
  //   ". button .";

  // column-gap: 10px;
  // row-gap: 20px;
  // same as:

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
}

#searchComp {
  grid-column: 1 /4;
  grid-row: 1/2;
  display: grid;

  grid: 1fr 1fr/1fr;
}
#display {
  background: #b47a57;

  border: #1f3657 solid 10px;
  border-radius: 5px;
  grid-column: 2 /3;
  grid-row: 2/3;
}
button {
  background: rgb(0, 0, 0);
  color: white;
  border-radius: 5px;
  transition: 0.3s ease-in-out;

  &:hover {
    background: #cc5a7194;
  }
  grid-column: 1 /4;
  grid-row: 3/4;
  width: 60%;
  height: 60%;
  justify-self: center;
  color: white;
  background: #cc5a71;
  border-radius: 5px;
  transition: 0.3s ease-in-out;
  font-weight: bold;
}
</style>
