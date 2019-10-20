<template lang="html">
  <div class="weather-search">
    <input type="text" name="" v-model='searchTerm'>
    <button type="button" name="button" v-on:click='handleSearch'>Search</button>
  </div>

</template>

<script>
import {eventBus} from '@/main.js'

export default {
  name: 'weather-search',
  data() {
    return {
      searchTerm: null
    }
  },
  methods: {
    handleSearch() {
      eventBus.$emit('weather-search', this.searchTerm);
    }
  }
}
</script>

<style lang="css" scoped>

  .weather-search {
    width: 31vh;
    display: flex;
    justify-content: space-between;
  }

</style>
