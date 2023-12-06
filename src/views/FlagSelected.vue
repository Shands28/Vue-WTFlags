<script setup lang="ts">
import {Country} from "../Interfaces/country";

const {flagSelected} = defineProps<{
  flagSelected: Country
}>()
</script>

<template>
  <div class="flag-container">
    <img :src="`https://flagcdn.com/${flagSelected.country_code}.svg`"
         alt="{{$t('flag_of')}} {{$t(flagSelected.country_code)}}">
  </div>
</template>

<style scoped>
img {
  border: 0;
  border-radius: 15px;
  width: 100%;
  box-shadow: 3px 0 #f44336, -3px 0 #00e5e5, 0 3px #e0ac08, 0 -3px #2dd36f,
  2px 2px #f44336, -2px -2px #00e5e5, 2px -2px #e0ac08, -2px 2px #2dd36f;
  background: #fff;
}
</style>
