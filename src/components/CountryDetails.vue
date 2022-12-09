<template>
  <div class="col-7">
    <img
      :src="`https://flagpedia.net/data/flags/icon/72x54/${country.alpha2Code.toLowerCase()}.png`"
      alt="country flag"
      style="width: 300px"
    />
    <h1>{{ country.name.common }}</h1>
    <table class="table">
      <thead></thead>
      <tbody>
        <tr>
          <td style="width: 30%">Capital</td>
          <td>{{ country.capital[0] }}</td>
        </tr>
        <tr>
          <td>Area</td>
          <td>{{ country.area }}<sup>2</sup></td>
        </tr>
        <tr>
          <td>Borders</td>
          <td>
            <ul>
              <li
                v-for="(border, index) of country.borders"
                :key="index"
                v-if="country.borders.length"
              >
                <a :href="border">{{ nameSearch(border) }}</a>
              </li>
              <li v-else>No borders</li>
            </ul>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>
<script>
import Countries from "../../public/countries.json";
export default {
  data() {
    return {
      countries: Countries,
    };
  },
  computed: {
    country() {
      return this.countries.find(
        (country) => country.alpha3Code === this.$route.params.alpha3Code
      );
    },
  },
  methods: {
    nameSearch(alpha3Code) {
      return this.countries.find((country) => country.alpha3Code === alpha3Code)
        .name.common;
    },
  },
  mounted() {
    // NO se tiene que hacer en mounted
    console.log(this.$route.params.alpha3Code);
  },
};
</script>
