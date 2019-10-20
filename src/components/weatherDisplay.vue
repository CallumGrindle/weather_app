<template lang="html">
  <article class="display">
    <div class="location">
      <h1 class='name'>{{weatherData.name}}</h1>
      <img class='icon' :src='this.iconUrl' >
    </div>
    <div class="temperature">
      <h2 class="degree">{{weatherData.main.temp}} °C</h2>
    </div>
    <div class="">
      <p>{{weatherData.weather[0].description}}</p>
    </div>
  </article>
</template>

<script>
export default {
  name: 'weather-display',
  props: ['weatherData'],
  data() {
    return {
      iconUrl: `http://openweathermap.org/img/wn/${this.weatherData.weather[0].icon}@2x.png`
    }
  }
}
</script>

<style lang="css" scoped>

  .display {
    font-family: Helvetica, sans-serif;
    display: flex;
    flex-direction: column;
  }

  .location {
    display: flex;
    justify-content: center;
  }

  h1.name {
    display: flex;
    flex-direction: column;
    justify-content: center;
  }

</style>
