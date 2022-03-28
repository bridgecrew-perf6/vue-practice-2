<template>
  <h2>Parent Component</h2>
  <input v-model="nickname" type="text" ref="inputRef" />
  <button @click="consoleRef">console.Ref</button>
  <hr />
  <ChildComp v-if="showchild" ref="childRef" />
  <button @click="showchild = false">Unmounted child</button>
</template>

<script>
import ChildComp from "./ChildComp.vue";
export default {
  name: "parentComp",
  data() {
    return { showchild: true, nickname: "" };
  },
  methods: {
    consoleRef() {
      console.log(this.$refs.inputRef, this);
      console.log(this.$refs.childRef, this);
      this.$refs.childRef.sayHello();
    },
  },
  components: {
    ChildComp,
  },
  beforeCreate() {
    console.log("parent before create");
  },
  created() {
    console.log("parent created");
  },
  beforeMount() {
    console.log("parent beforeMount");
  },
  mounted() {
    console.log("parent mounted");
  },
  updated() {
    console.log("parent updated");
  },
  beforeUnmount() {
    console.log("parent beforeUnmount");
  },
  unmounted() {
    console.log("parent unmounted");
  },
};
</script>

<style></style>
