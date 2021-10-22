<template>
  <main v-if="loading">
    <div class="flex justify-center items-center">
      <div
        class="
          animate-spin
          rounded-full
          h-32
          w-32
          border-t-2 border-b-2 border-blue-800
        "
      ></div>
    </div>
  </main>
  <main v-else>
    <DataTitle :text="title" :dataDate="dataDate" />
    <DataBoxes :stats="stats" />
  </main>
</template>
<script>
import DataTitle from "../components/DataTitle.vue";
import DataBoxes from "../components/DataBoxes.vue";

export default {
  name: "Home",
  components: {
    DataTitle,
    DataBoxes,
  },
  data() {
    return {
      loading: true,
      title: "Global",
      dataDate: "",
      stats: {},
      countries: [],
    };
  },
  methods: {
    async fetchCovidData() {
      const res = await fetch("https://api.covid19api.com/summary");
      const data = await res.json();
      return data;
    },
  },
  async created() {
    const data = await this.fetchCovidData();

    this.dataDate = data.Date;
    this.stats = data.Global;
    this.countries = data.Countries;
    this.loading = false;
  },
};
</script>
