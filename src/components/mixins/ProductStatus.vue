<template>
  <h2>전체금액 {{ totalMoney }}</h2>
  <div>
    <button @click="addMoney(100)">100</button>
    <button @click="addMoney(200)">200</button>
    <button @click="addMoney(300)">300</button>
    <button @click="addMoney(400)">400</button>
    <button @click="addMoney(500)">500</button>
  </div>
</template>

<script>
import useMoney from "../../composables/useMoney";
export default {
  name: "productStatus",
  setup() {
    const { addMoney, totalMoney } = useMoney();

    return {
      addMoney,
      totalMoney,
    };
  },
};
</script>

<style></style>
