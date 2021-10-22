<template>
  <div class="grid md:grid-cols-2 gap-4">
    <div class="shadow-md bg-blue-300 p-10 text-center rounded">
      <h3 class="text-3xl text-blue-900 font-bold mb-4">Cases</h3>
      <div class="text-2xl mb-4">
        <span class="font-bold">New: </span>
        {{ formatData(stats.NewConfirmed) }}
      </div>
      <div class="text-2xl mb-4">
        <span class="font-bold">Total: </span>
        {{ formatData(stats.TotalConfirmed) }}
      </div>
    </div>
    <div class="shadow-md bg-blue-300 p-10 text-center rounded">
      <h3 class="text-3xl text-blue-900 font-bold mb-4">Deaths</h3>
      <div class="text-2xl mb-4">
        <span class="font-bold">New: </span>
        {{ formatData(stats.NewDeaths) }}
      </div>
      <div class="text-2xl mb-4">
        <span class="font-bold">Total: </span>
        {{ formatData(stats.TotalDeaths) }}
      </div>
    </div>
  </div>
</template>

<script>
import numeral from "numeral";
export default {
  name: "DataBoxes",
  props: ["stats"],
  methods: {
    formatData(x) {
      return numeral(x).format("0,0");
    },
  },
};
</script>
