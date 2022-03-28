<template>
  <h2>isHandsome? {{ name }}</h2>
  <button @click="changeName">ChangeUsername</button>
  <h2>제품명: {{ model }}, 가격 {{ price }}</h2>
  <button @click="changeProduct">제품바꾸기</button>

  <div>
    <input type="text" v-model="name" />
  </div>
  <hr />
  <div>
    price <input type="number" v-model="price" /> amount
    <input type="number" v-model="amount" />
    <h3>Total Price :: {{ totalPrice }}</h3>
  </div>
  <hr />
  <div>
    first <input type="text" v-model="home.city" /> last
    <input type="text" v-model="last" />
    <h3>Full Name :: {{ fullName }}</h3>
  </div>
  <!-- <input type="text" ref="inputRef" /> -->
  <ChildComponent
    firstname="Park"
    lastname="suncheol"
    @sendParent="sendParent"
  />
  <hr />
  <FeeStatus />
  <hr />
  <ProductStatus />
  <hr />
  <SavingStatus />
</template>

<script>
import FeeStatus from "../mixins/FeeStatus.vue";
import ProductStatus from "../mixins/ProductStatus.vue";
import SavingStatus from "../mixins/SavingStatus.vue";
import ChildComponent from "./ChildComponent.vue";
import { reactive, toRefs, ref, computed, watch } from "vue";
export default {
  name: "TestComponent",
  components: { ChildComponent, FeeStatus, ProductStatus, SavingStatus },
  methods: {
    sendParent() {
      console.log("evnet!");
    },
  },

  setup() {
    const name = reactive({
      first: "Park",
      last: "Suncheol",
      home: {
        city: "seoul",
        type: "apt",
      },
    });
    const fullName = computed(function () {
      return `${name.first} ${name.last}`;
    });
    watch(
      () => {
        return name.first;
      },
      (newValue, oldValue) => {
        console.log(newValue, oldValue);
      }
    );
    watch(
      () => {
        return { ...name.home };
      },
      (newValue, oldValue) => {
        console.log(newValue, oldValue);
      },
      { deep: true }
    );

    const totalPrice = computed(() => {
      return price.value + amount.value;
    });

    const price = ref(5000);
    const amount = ref(1);
    const product = reactive({
      model: "Tv",
      price: 100,
    });
    function changeProduct() {
      product.model = "세탁기";
      product.price = 1000;
    }
    watch(price, (newValue, oldValue) => {
      console.log(newValue, oldValue);
    });

    const state = reactive({
      name: "suncheol",
      age: 22,
      job: "programmer",
    });
    function changeName() {
      state.name = "Jisung";
    }
    return {
      ...toRefs(state),
      ...toRefs(product),
      ...toRefs(name),
      changeName,
      changeProduct,
      price,
      amount,
      totalPrice,
      fullName,
    };
  },
};
</script>

<style></style>
