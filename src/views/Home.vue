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
    <CountrySelect @get-country="getCountryData" :countries="countries" />
    <div class="flex justify-center items-center">
      <button
        v-if="stats.Country"
        class="
          bg-green-700
          text-white
          rounded
          p-3
          mt-10
          focus:outline-none
          hover:bg-green-600
        "
        @click="onClick"
      >
        Clear Country
      </button>
    </div>
  </main>
</template>
<script>
import DataTitle from "../components/DataTitle.vue";
import DataBoxes from "../components/DataBoxes.vue";
import CountrySelect from "../components/CountrySelect.vue";

export default {
  name: "Home",
  components: {
    DataTitle,
    DataBoxes,
    CountrySelect,
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

    getCountryData(country) {
      this.stats = country;
      this.title = country.Country;
    },
    async onClick() {
      this.loading = true;
      const data = await this.fetchCovidData();
      this.title = "Global";
      this.stats = data.Global;
      this.loading = false;
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
