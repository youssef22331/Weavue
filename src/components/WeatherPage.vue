<script setup lang="ts">
import WeatherCard from './WeatherCard.vue';
import { cities } from '@/stores/cityStore';
import { location } from '@/stores/locationStore';
import { onMounted } from 'vue';


onMounted(() => {
  //console.log('weather page mounted with this cities', cities.list)
});
</script>
<template>
  <section class="flex max-w-[1800px] px-6 mx-auto justify-start w-full pb-[80px]">
    <div class="weather-card-row flex justify-start gap-2 w-full flex-wrap">
      <WeatherCard v-if="location.lat && location.long" :lat="location.lat" :long="location.long" />
      <WeatherCard v-for="(city, index) in cities.list" :key="index" :cityName="city" />
    </div>
  </section>
</template>
<style lang="scss">
.weather-card-row {
  @media (max-width: 767px) {
    flex-direction: column-reverse;
    align-items: center;
  }
}
</style>
