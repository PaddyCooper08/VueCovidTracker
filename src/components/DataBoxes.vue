<template>
  <div class="grid md:grid-cols-2 gap-4">
    <div class="shadow-md bg-blue-300 p-10 text-center rounded">
      <h3 class="text-3xl text-blue-900 font-bold mb-4">Cases</h3>
      <div class="text-2xl mb-4">
        <span class="font-bold">New: </span>
        {{ formatNewConfirmed }}
      </div>
      <div class="text-2xl mb-4">
        <span class="font-bold">Total: </span>
        {{ formatTotalConfirmed }}
      </div>
    </div>
    <div class="shadow-md bg-blue-300 p-10 text-center rounded">
      <h3 class="text-3xl text-blue-900 font-bold mb-4">Deaths</h3>
      <div class="text-2xl mb-4">
        <span class="font-bold">New: </span>
        {{ formatNewDeaths }}
      </div>
      <div class="text-2xl mb-4">
        <span class="font-bold">Total: </span>
        {{ formatTotalDeaths }}
      </div>
    </div>
  </div>
</template>

<script>
import numeral from "numeral";
export default {
  name: "DataBoxes",
  props: ["stats"],
  computed: {
    formatNewConfirmed: function () {
      return numeral(this.stats.NewConfirmed).format("0,0");
    },
    formatTotalConfirmed: function () {
      return numeral(this.stats.TotalConfirmed).format("0,0");
    },
    formatNewDeaths: function () {
      return numeral(this.stats.NewDeaths).format("0,0");
    },
    formatTotalDeaths: function () {
      return numeral(this.stats.TotalDeaths).format("0,0");
    },
  },
};
</script>
