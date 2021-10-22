<template>
  <select
    v-model="selected"
    class="
      text-blue-900
      form-select
      mt-10
      block
      w-full
      border
      p-3
      rounded
      border-blue-300
    "
    @change="onChange()"
  >
    <option value="0">Select Country</option>
    <option :value="country.ID" v-for="country in countries">
      {{ country.Country }}
    </option>
  </select>
</template>
<script>
export default {
  name: "CountrySelect",
  props: ["countries"],
  data() {
    return {
      selected: 0,
    };
  },
  methods: {
    onChange() {
      const country = this.countries.find((item) => item.ID === this.selected);

      this.$emit("get-country", country);
    },
  },
};
</script>
