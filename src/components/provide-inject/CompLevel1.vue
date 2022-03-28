<template>
  <h2>component1</h2>
  <CompLevel2 />
</template>

<script>
import CompLevel2 from "./CompLevel2.vue";
export default {
  name: "CompLevel1",
  components: {
    CompLevel2,
  },
};
</script>

<style></style>
