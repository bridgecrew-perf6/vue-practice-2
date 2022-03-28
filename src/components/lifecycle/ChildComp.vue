<template>
  <h2>Child Component</h2>
  <input type="text" v-model="username" />
</template>

<script>
export default {
  name: "childComp",
  data() {
    return {
      username: "",
    };
  },
  methods: {
    sayHello() {
      console.log("say Hello!");
    },
  },
  beforeCreate() {
    console.log("child before create");
  },
  created() {
    console.log("child created");
  },
  beforeMount() {
    console.log("child beforeMount");
  },
  mounted() {
    console.log("child mounted");
  },
  updated() {
    console.log("child updated");
  },
  beforeUnmount() {
    console.log("child beforeUnmount");
  },
  unmounted() {
    console.log("child unmounted");
  },
};
</script>

<style></style>
