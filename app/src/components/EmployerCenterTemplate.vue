<template>
  <li>
    <p>Адреса: {{ gasStation.adress }}</p>
    <p>Власник: {{ gasStation.firm_owner }}</p>

    <p>Залишок А80: {{ gasStation.rest_A80.toFixed(2) }} л.</p>
    <p>Залишок А92: {{ gasStation.rest_A92.toFixed(2) }} л.</p>
    <p>Залишок А95: {{ gasStation.rest_A95.toFixed(2) }} л.</p>

    <p>Ціна А80: {{ gasStation.price_A80.toFixed(2) }} грн.</p>
    <p>Ціна А92: {{ gasStation.price_A92.toFixed(2) }} грн.</p>
    <p>Ціна А95: {{ gasStation.price_A95.toFixed(2) }} грн.</p>
  </li>
</template>

<script>
export default {
  name: "GasStation",
  props: {
    gasStation: Object,
  },
  data() {
    return {};
  },
};
</script>

<style scoped>
</style>>

