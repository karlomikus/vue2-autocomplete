
<template>
  <div>
    <label for="search-1">Seach places</label>
    <autocomplete
      id="search-1"
      url="https://maps.googleapis.com/maps/api/geocode/json?address="
      :custom-params="{ token: 'dev' }"
      anchor="formatted_address"
      label="formatted_address"
      :process="processJSON"
      :on-select="getData">
    </autocomplete>
    <hr>
    <label for="search-2">Debounce data</label>
    <autocomplete
      id="search-2"
      url="https://maps.googleapis.com/maps/api/geocode/json?address="
      :custom-params="{ token: 'dev' }"
      anchor="formatted_address"
      label="formatted_address"
      :process="processJSON"
      :on-select="getData"
      :debounce="1000">
    </autocomplete>
    <pre>
      {{ place.formatted_address }}
    </pre>
  </div>
</template>

<script>

  import Autocomplete from './vue-autocomplete.vue';
  require("../../../dist/style/vue2-autocomplete.css")

  export default {
    components: { Autocomplete },

    data() {
      return {
        place: {}
      }
    },

    methods: {
      processJSON(json) {
        return json.results;
      },
      getData(data) {
        this.place = data
      }
    }
  };

</script>
