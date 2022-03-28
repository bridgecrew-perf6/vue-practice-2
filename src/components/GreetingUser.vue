<template>
  <div>
    <h2 v-bind="$attrs">Hello!!</h2>
    <h3>환영합니다 {{ name }}님</h3>
  </div>
</template>
<script>
export default {
  name: "GreetingUser",
  inheritAttrs: false,
  props: {
    name: {
      type: String,
      default: "user",
    },
  },
};
</script>
<style scoped></style>
