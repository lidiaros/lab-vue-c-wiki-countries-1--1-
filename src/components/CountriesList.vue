<template>
  <div class="container">
    <!-- Bootstrap row wrapper div -->
    <div class="row">
      <div class="col-5" style="max-height: 90vh; overflow: scroll">
        <div class="list-group">
          <!-- <div v-for="(country, index) of countries" :key="index">
            {{ country }}
          </div> -->
          <router-link
            v-for="(country, index) of countries"
            :key="index"
            :to="`/list/${country.alpha3Code}`"
          >
            <img
              :src="`https://flagpedia.net/data/flags/icon/72x54/${country.alpha2Code.toLowerCase()}.png`"
            />
            <p>{{ country.name.common }}</p>
          </router-link>
        </div>
      </div>
      <RouterView />
    </div>
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
};
</script>
