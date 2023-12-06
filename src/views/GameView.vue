<script setup lang="ts">
import FlagSelected from "@/views/FlagSelected.vue";
import {Country} from "../Interfaces/country";

const flagSelected: Country = {country_code: 'es', name: 'Spain', weight: 1};

</script>

<template>
<FlagSelected :flagSelected="flagSelected"/>
</template>

<style scoped>

</style>
